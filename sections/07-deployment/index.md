---
title: Deployment
has_children: false
nav_order: 8
---

# Deployment
This section explains how to set up **MyStudyAgenda** on a local machine. Here are offered three ways to install the software, ranging from a quick package installation to a full development setup.

### General Prerequisites
- **Python 3.10, 3.11, or 3.12** installed on your system.

    Python can be installed from the official website or via a package manager. The required version range is specified in the project configuration (the recommended python version is [3.11](https://www.python.org/downloads/release/python-31114/)).

   The user can verify the version of python already installed in its machine using the command

   ```bash
   python --version

## 1. Standard Installation (Recommended)
The easiest way to install the application is via **TestPyPI**. This method automatically handles dependencies without requiring you to download the source code manually.

### Steps
1. **Create a virtual environment (Optional but recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate # On Linux and MacOS, or
   source venv\Scripts\activate # On Windows

2. **Install from TestPyPI:** Since the project is hosted on the TestPyPI repository, use the following command:
    ```bash
    pip install -i https://test.pypi.org/simple/ mystudyagenda

3. **Run the application**:
    ```bash
    python -m MyStudyAgenda

## 2. Manual Release Download
If you prefer not to use a package manager, you can download the source artifacts directly from the project's GitHub repository.

1. Go to the [GitHub Releases](https://github.com/unibo-dtm-se-2425-MyStudyAgenda/artifact/releases) page.
2. Download the .zip or .tar.gz archive from the latest version tag.
3. Extract the archive.
4. Install the requirements and run as described in the section below.

## 3. Developer Installation (Source Code)
Use this method if you want to modify the code or contribute to the project. This requires Poetry, the project's dependency manager.

### Prerequisites:
* Python 3.11 (Recommended)
* Git
* Poetry (Install via `pip install poetry`)

### Steps:
1. **Clone the repository:**
    ```bash
    git clone https://github.com/unibo-dtm-se-2425-MyStudyAgenda
    cd artfact

2. **Install project dependencies:**
Poetry will create a virtual environment and install Kivy, KivyMD, and other required libraries automatically.
    ```bash
    poetry install

3. **Make sure the application can run correctly on your local environment**:
Run the test suite to confirm the environment is correctly set and ready to run the software.
    ```bash
    poetry run pytest

4. **Running the application:**
    ```bash
    poetry run python -m app.main
    ```
    If commands 3 and 4 do not work, make sure to run them in the `artifact` directory of the repository.


## Server-side installation
The application does not require any server-side installation.

MyStudyAgenda is a standalone desktop application:
- it does not expose APIs
- it does not rely on backend services
- it does not require deployment on a remote server

Moreover, the application uses a **local SQLite database**, which is automatically created and managed on the user's machine.