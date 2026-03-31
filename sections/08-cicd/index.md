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
- **GUI tests** for the Kivy-based user interface
- Tests across:
  - multiple operating systems (Linux, Windows, macOS)
  - multiple Python versions (3.10, 3.11, 3.12)

The CI workflow is triggered on:
- every `push` (excluding documentation-only files),
- every `pull_request`,
- manual execution (`workflow_dispatch`).

### Why

Automating testing ensures that:
- platform-specific issues are detected early,
- GUI-related regressions are caught despite the graphical nature of the application,
- changes merged into the main branch preserve functional correctness.

Given the complexity of testing a GUI framework like **Kivy**, the CI pipeline explicitly separates **logic tests** from **GUI tests**.

### How

The CI workflow is defined in `check.yml` and is split into two jobs.

#### Unit Tests Job

- Runs on **Linux, Windows, and macOS**
- Uses a **matrix strategy** for Python versions
- Installs system-level dependencies required by Kivy (on Linux only)
- Installs project dependencies via **Poetry**
- Executes tests marked as *non-UI*:

    ```bash
    pytest -m "not ui"
    ```

This job focuses on:
- business logic,
- persistence layer,
- controllers,
- non-graphical components.

GUI Tests Job
- Runs only if unit tests succeed
- Executes on Ubuntu for maximum stability
- Uses Xvfb (X virtual framebuffer) to simulate a display server
- Runs tests explicitly marked as UI tests:
    ```bash
    xvfb-run -a pytest -m "ui"
    ```

This approach allows automated testing of Kivy screens and widgets in a headless CI environment.

#### Environment variables

Several environment variables are configured to adapt Kivy to CI execution:

`KIVY_NO_ARGS=1` – prevents Kivy from parsing command-line arguments

`KIVY_NO_CONSOLELOG=1` – disables verbose logging

`KIVY_LOG_LEVEL=error` – reduces log noise

`PYTHONPATH=.` – ensures correct module resolution

`CI=true` – signals execution inside a CI environment

Dependency caching is also enabled to speed up repeated workflow runs.

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
* `TEST_PYPI_TOKEN`,which is used to authenticate the publication to TestPyPI
* `GITHUB_TOKEN`, which is automatically provided by GitHub Actions and used to create GitHub Releases