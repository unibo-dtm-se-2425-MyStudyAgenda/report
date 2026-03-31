---
title: Release
has_children: false
nav_order: 7
---
# Release

## Produced artefacts

The project produces a single software artefact: a Python application called **MyStudyAgenda**.
The application is packaged as a Python package using **Poetry**, which generates both a source
distribution (`sdist`) and a built distribution (`wheel`).

No additional artefacts (e.g. Docker images or separate libraries) are produced, since the project
is designed as a single, self-contained desktop application.


## Distribution platforms

The artefact is intended to be released on **TestPyPI**.
This choice allows validating the packaging and release process in a safe environment before
publishing on the official PyPI repository.

Additionally, each release is published as a **GitHub Release**, which contains:
- the packaged artefacts
- the corresponding version tag
- the changelog associated with the release

GitHub was chosen because it is the main repository hosting the project and integrates seamlessly
with GitHub Actions.

---

## Release process

The release process is **manual but automated**.

A dedicated GitHub Actions workflow (`deploy.yml`) is responsible for building and releasing the
artefacts. The workflow is triggered only when:
- a version tag following semantic versioning (e.g. `v0.1.0`) is pushed, or
- the workflow is manually triggered via `workflow_dispatch`.

The release workflow performs the following steps:
1. checks out the repository
2. sets up a stable Python environment
3. installs dependencies using Poetry
4. builds the Python package
5. publishes the artefact to TestPyPI
6. creates a GitHub Release associated with the version tag

This approach ensures that releases are reproducible, traceable, and consistent with the CI pipeline.

## Choice of the license

The project adopts the **MIT License** for both the source code and the released artefacts.

The MIT License was chosen because it is:
- permissive
- simple to understand
- widely adopted in open-source Python projects

It allows reuse, modification, and redistribution of the software with minimal restrictions.

## Choice of the versioning schema

The project follows **Semantic Versioning (SemVer)**.

Each version is expressed in the form MAJOR.MINOR.PATCH, where

- MAJOR versions indicate incompatible or major changes
- MINOR versions introduce new features while maintaining backward compatibility
- PATCH versions contain bug fixes and small improvements

Since the project produces a single artefact, a single version number is used for the entire system.

## Creating a new release

The project follows a lightweight but structured release process.

Before creating a new release, the `CHANGELOG.md` file is manually updated to summarize
the changes introduced since the previous version. Each release entry follows the
Semantic Versioning convention and includes a brief description of new features,
improvements, and fixes.

Once the changelog is updated, the version number in `pyproject.toml` is aligned with
the intended release version. A Git tag matching the version number (e.g. `v0.1.0`)
is then created and pushed to the remote repository (with the terminal commands `git tag v0.1.0` and `git push origin v0.1.0` respectively).

Pushing the tag automatically triggers the release workflow, which builds and publishes the artefact
and creates a corresponding GitHub Release.

Pushing a version tag automatically triggers the Continuous Deployment workflow,
which builds and publishes the artefact
and creates a corresponding GitHub Release using the contents of the `CHANGELOG.md`.