---
title: Developer guide
has_children: false
nav_order: 11
---

# Developer Guide
Welcome to the MyStudyAgenda development team! This guide outlines the technical and organizational standards required to maintain the integrity of this desktop application.

## Organizational Information
The project is managed entirely on GitHub, which serves as both the code repository and the communication platform.

To maintain a transparent development process, all communication regarding bugs or feature requests must be centralized through our GitHub Issues page. When reporting a problem, please include steps to reproduce the behavior and information about your operating system.

For direct collaboration or urgent team coordination, please contact the lead maintainer directly via their [GitHub profile](https://github.com/annacampagna) or via e-mail (anna.campagna3@studio.unibo.it)

## Coding Standards and Conventions
We follow PEP 8 standards for Python code style. To ensure consistency, we use descriptive `snake_case` for function and variable names, while classes must use `PascalCase`.

Beyond formatting, every new logic component must be accompanied by unit tests. If you are modifying the UI, you must verify that the Kivy widgets remain responsive across different window sizes.

Before committing, run `poetry run pytest` (in the `artifact` directory) to ensure that both logic and GUI tests pass within your local environment.

## Development Environment
Please find detailed instructions about how to clone the repository and set up the development environment at **Section 7 (Deployment)** of this report.

## Development Workflow
To keep the main branch stable,  please follow a Feature Branch workflow, as described in the steps below:
1. Create a new branch from `main`:
Before starting new work, ensure your local main branch is up to date and create a scoped branch. Using a naming convention like `feature/` or `bugfix/` helps the team identify the purpose of the branch at a glance.
    ```bash
    # Ensure you are on main and have the latest changes
    git checkout main
    git pull origin main

    # Create and switch to a new feature branch
    git checkout -b feature/your-feature-name
    ```

2. Impementation:
As you develop, you must regularly validate that your logic and UI components remain stable running the test suite.
    ```bash
    poetry run pytest
    ```

3. Pull Request Preparation:
Once your code passes local tests, push your branch to the remote repository. This will trigger the CI workflow (`check.yml`), which validates your code across Ubuntu, Windows, and macOS using Python versions 3.10 through 3.12.
    ```bash
    # Stage your changes
    git add .

    # Commit with a descriptive message
    git commit -m "feat: add specific functionality and corresponding tests"

    # Push to GitHub to trigger the CI pipeline
    git push origin feature/your-feature-name
    ```

4. Pull Request and Peer Review
After pushing your branch, navigate to the GitHub repository and open a Pull Request (PR) against the `main` branch.
A project maintainer will review your logic, code style, and test coverage. If the maintainer requests changes, apply them locally, commit, and push again; the PR will update automatically.

5. Relese (Authorized Maintainers Only)
When a feature is merged and a new version is ready, maintainers trigger the CD workflow (`deploy.yml`) by pushing a version tag.

Our repository is equipped with GitHub Actions that trigger on every push and pull request. The CI workflow (check.yml) enforces quality by running a matrix of Python versions and operating systems. The CD workflow (deploy.yml) is reserved for releases; when a version tag like v1.0.0 is pushed, the system automatically builds the package and publishes it to TestPyPI. **Please do not manually push tags unless you are authorized to manage official releases.**

## Development Tools
* Recommended IDE: Visual Studio Code, as it is intuitive to use and it works well with Python and Git.
* Command line: when in your preferred IDE, open the terminal to use the Command Line Interface and run the commands cited in this report.

Please note that many instructions (e.g., staging changes, adding a commit message, etc.) have been described here as commands to perform in the command line because they universally work independently of the used IDE. However, many IDEs (such as Visual Studio Code) provide intuitive GUIs to perform the same actions. 