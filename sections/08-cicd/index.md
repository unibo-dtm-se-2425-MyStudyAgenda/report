---
title: CI/CD
has_children: false
nav_order: 9
---

# CI/CD

This section describes the Continuous Integration (CI) and Continuous Deployment (CD) pipeline adopted for the **MyStudyAgenda** project, implemented using **GitHub Actions**.

The main goals of the CI/CD workflow are:
- to automatically verify code correctness on multiple platforms and Python versions,
- to ensure regression-free evolution of the project,
- to support a controlled and reproducible release process.

## Continuous Integration (CI)

### What is automated

The CI pipeline automatically executes:

- **Unit tests** for model, DAO, controller, and non-GUI logic
- Tests across:
  - multiple operating systems (Linux, Windows, macOS)
  - multiple Python versions (3.10, 3.11, 3.12)

While it skips **GUI tests** for the Kivy-based user interface, as GUI tests require a window provider and OpenGL context, which are not available in headless CI environments.

The CI workflow is triggered on:
- every `push` (excluding documentation-only files),
- every `pull_request`,
- manual execution (`workflow_dispatch`).

### Why

Automating testing ensures that:
- platform-specific issues are detected early,
- changes merged into the main branch preserve functional correctness.

### How

The CI workflow is defined in `check.yml` and consists of a single, comprehensive testing job.

#### Test Job

- Runs on **Linux, Windows, and macOS**
- Uses a **matrix strategy** to test across Python versions 3.10, 3.11, and 3.12
- Installs essential system-level dependencies required by Kivy on Linux runners, such as `libsdl2-dev` and `libgl1-mesa-dev`
- Manages environment isolation and project dependencies via **Poetry**
- Executes the full suite of tests using `pytest`:

    ```bash
    poetry run pytest
    ```

This job focuses on validating:
- business logic (Model layer),
- persistence layer (DAO),
- controllers,
- non-graphical components and general logic,
- system functioning through all the layers.

#### Environment variables

Several environment variables are configured to adapt Kivy to CI execution:

`KIVY_NO_ARGS=1` – prevents Kivy from parsing command-line arguments

`KIVY_BACKEND=offscreen` – forces Kivy to use an offscreen rendering backend, bypassing the need for a display server

`PYTHONPATH=.` – ensures correct module resolution so that the package can be imported during testing

`CI=true` – signals execution inside a CI environment

The job also includes a concurrency configuration to automatically cancel redundant runs on the same branch or PR, optimizing resource usage.

## Continuous Deployment (CD)

### What is automated
The CD pipeline automates the release process by:
- building the application as a Python package,
- publishing it to TestPyPI,
- creating a GitHub Release with attached artefacts.

The workflow is triggered when a Git tag matching the pattern `v*.*.*` is pushed, or manually via workflow_dispatch.

### Why
This approach ensures that:
- only explicitly versioned releases are deployed,
- releases are reproducible and traceable,
- packaging and publication steps are consistently executed.

TestPyPI is used instead of the production PyPI repository to safely validate the release pipeline without publishing final artefacts publicly.

### How
The CD workflow is defined in deploy.yml and performs the following steps:
1. Checkout the full Git history (required for tagging and release metadata)
2. Set up Python 3.11
3. Install dependencies using Poetry
4. Build the package (`sdist` and `wheel`)
5. Configure the TestPyPI repository
6. Publish the package to TestPyPI
7. Create a GitHub Release associated with the version tag

### Secrets and permissions
The CD pipeline relies on two main secrets:
* `TEST_PYPI_TOKEN`, which is used to authenticate the publication to TestPyPI
* `GITHUB_TOKEN`, which is automatically provided by GitHub Actions and used to create GitHub Releases