![image](https://github.com/user-attachments/assets/6c813200-6ff4-4ad3-a193-7b2d8cde7718)


| Author          | Created On  | Version   | Last Updated By | Last Edited On |
|-----------------|-------------|-----------|------------------|----------------|
| Pravalika   | 2025-04-17  | Version 1 |Pravalika | 2025-04-17     |


## 📚 Table of Contents

- [📖 What is Poetry?](#what-is-poetry)

- [💡 Its Role in Modern Python Project Management](#-its-role-in-modern-python-project-management)
  - [Dependency Management](#dependency-management)
  - [Virtual Environment Handling](#virtual-environment-handling)
  - [Project Initialization](#project-initialization)
  - [Packaging and Publishing](#packaging-and-publishing)
  - [Versioning and Release Management](#versioning-and-release-management)

- [🔁 Replaces Traditional Tools Like](#-replaces-traditional-tools-like)

- [🔧 Why Use Poetry?](#-why-use-poetry)
  - [Avoids Manually Creating requirements.txt, setup.py, etc.](#avoids-manually-creating-requirementstxt-setuppy-etc)
  - [Ensures Reproducible Builds with poetry.lock](#ensures-reproducible-builds-with-poetrylock)
  - [Simplifies Virtual Environment Handling](#simplifies-virtual-environment-handling)

- [✅ Purpose of Using Poetry](#-purpose-of-using-poetry)

- [✅ Prerequisites](#-prerequisites)

- [✨ Key Features of Poetry](#-key-features-of-poetry)

- [🛠️ Installation Guide](#️-installation-guide)
  - [Install via curl](#install-via-curl)
  - [Add Poetry to PATH](#add-poetry-to-path)
  - [Check Poetry Version](#check-poetry-version)

- [📘 Basic Usage](#-basic-usage)
  - [Create a New Project](#create-a-new-project)
  - [Add, Install, and Remove Dependencies](#add-install-and-remove-dependencies)
  - [Using the Virtual Environment](#using-the-virtual-environment)
  - [Build the Package](#build-the-package)

- [🔍 Comparison: Poetry vs pip + venv](#-comparison-poetry-vs-pip--venv)

- [🧠 Best Practices](#-best-practices)

- [🛠️ Troubleshooting](#️-troubleshooting)

- [📧 Contact Information](#-contact-information)

- [📚 Reference](#-reference)













## What is Poetry?

### 📖 Definition

**Poetry** is a Python dependency management and packaging tool that simplifies the way developers build, manage, and distribute Python projects. It provides a standardized and streamlined workflow for everything from dependency installation to package publishing.

In simpler terms, **Poetry** is like a project manager for Python—handling your project's environment, dependencies, versioning, and publishing in a single unified tool.

It centers its configuration in a single file: **`pyproject.toml`**, which becomes the source of truth for your project’s metadata, dependencies, scripts, and more.


## 💡 Its Role in Modern Python Project Management

In modern Python development, managing environments, dependencies, and packaging can get messy fast—especially in larger projects or teams. This is where **Poetry** shines:

### 1. **Dependency Management**
- **Poetry** allows you to declare the packages your project needs in a clean and easy-to-read format. It resolves and installs dependencies reproducibly, ensuring your project works the same way across different machines and environments.
- Instead of `requirements.txt`, you use `pyproject.toml` and `poetry.lock`.
- It **separates** development and runtime dependencies.
- Automatically handles **dependency conflicts** with smart resolution.

### 2. **Virtual Environment Handling**
- **Poetry** automatically creates and manages virtual environments for each project. No need to manually use `python -m venv` or activate environments—it just works.
- Keeps your global Python environment **clean**.
- Ensures **isolated** and **reproducible builds**.

### 3. **Project Initialization**
- Starting a new project? `poetry new` or `poetry init` sets up a fully-structured Python project with best practices baked in—ideal for open-source packages or enterprise codebases.
- Creates standard folders like `tests/`, `src/`, and initial config files.
- Encourages good **project structure** from the beginning.

### 4. **Packaging and Publishing**
- **Poetry** makes it simple to build and publish Python packages to PyPI or a private repository.
- Use `poetry build` to package.
- Use `poetry publish` to upload to PyPI (with authentication).

### 5. **Versioning and Release Management**
- **Poetry** supports **semantic versioning** and allows for automatic version bumps, changelogs, and more. It's great for projects following a **release cadence**.

## 🔁 Replaces Traditional Tools Like:

| Traditional Tool     | Poetry Replacement / Feature                                           |
|----------------------|------------------------------------------------------------------------|
| **pip**              | `poetry add`, `poetry install` handles installs, version pinning       |
| **venv / virtualenv**| Poetry automatically manages virtual environments                      |
| **setuptools**       | Handled via `pyproject.toml` (build metadata), no manual setup needed |
| **requirements.txt** | Uses `pyproject.toml` and `poetry.lock` instead                        |
| **twine**            | Replaced with `poetry publish` for publishing packages                 |


## Why Use Poetry?

### 🔧 Avoids Manually Creating `requirements.txt`, `setup.py`, etc.

In traditional Python project setups, you’d often need to manually create and maintain several files to manage dependencies and project metadata. With **Poetry**, this process is streamlined:

- **`requirements.txt`**: Instead of manually listing all your dependencies and versions in a `requirements.txt` file, **Poetry** uses a single file: `pyproject.toml`. This file contains all the information about your dependencies, versioning, and project metadata. Poetry handles all the dependency installation and version pinning automatically.

  When you add a new dependency, you simply run `poetry add <package_name>`, and Poetry updates the `pyproject.toml` for you.

  **Poetry** also generates a `poetry.lock` file, ensuring consistency across environments and installs, as it locks the exact versions of dependencies.

- **`setup.py`**: Traditionally, packaging a Python project requires a `setup.py` file, which contains metadata about your project (name, version, author, etc.). **Poetry** eliminates the need for this by including all this information in `pyproject.toml`, simplifying the setup for your package and reducing boilerplate code.

## 🔄 Ensures Reproducible Builds with `poetry.lock`

One of the key challenges in Python dependency management is ensuring that your project behaves consistently across different environments and machines. Dependencies often have complex version requirements, and even a minor version change can cause unexpected behavior.

**Poetry** uses a `poetry.lock` file to lock down the exact versions of all dependencies. This means:

- When another developer installs your project, **Poetry** will use the `poetry.lock` file to install the exact same versions of dependencies that you used.
- Even if the upstream libraries release new versions or patches, the lock file ensures the project stays stable with the exact versions you specified.

## 🧰 Simplifies Virtual Environment Handling

Managing virtual environments is a common pain point for Python developers. Before **Poetry**, you might have had to manually create a virtual environment using `python -m venv`, activate it, and then install dependencies using `pip`.

With **Poetry**, virtual environments are handled automatically:

- **Automatic Virtual Environment Creation**: When you run `poetry install`, **Poetry** creates a virtual environment if one doesn’t exist already. You no longer need to manually create or activate virtual environments.
  
- **Environment Isolation**: **Poetry** ensures each project has its own isolated environment, so there are no conflicts with dependencies from other projects. This is especially helpful when working on multiple projects that may require different versions of Python or libraries.

- **No Need for pip or virtualenv**: **Poetry** integrates the functionality of both `pip` and `virtualenv` into a single tool. You don’t need to worry about manually managing virtual environments or updating `requirements.txt` files.





## ✅  Purpose of Using Poetry

The main purpose of **Poetry** is to simplify and streamline Python project management.

### 🎯 Goals:

- 🔄 **Replace multiple tools** (`pip`, `venv`, `setup.py`, `requirements.txt`, `twine`) with one unified tool.
- 📦 **Manage dependencies** in a declarative and reproducible way.
- ⚙️ **Automatically handle virtual environments** per project—no more manual `venv` setup.
- 🚀 **Simplify publishing** your packages directly to PyPI.
- 📁 **Use `pyproject.toml`** as a clean, standard, and centralized configuration file.


## ✅  Prerequisites

Before using Poetry, ensure your system meets the following requirements:

| Category                     | Requirement / Notes                                                                 |
|-----------------------------|--------------------------------------------------------------------------------------|
| 🧑‍💻 **Basic System Requirements** | - Python installed (3.7+ recommended)  <br> - Check with `python --version` or `python3 --version` <br> - `pip` installed (optional, but sometimes used alongside) <br> - Internet access to install Poetry and fetch packages |
| 💻 **Operating System Compatibility** | - Works on **Windows**, **macOS**, and **Linux**                                             |
| 🔧 **Optional**              | - Familiarity with the **command line** <br> - **Git** (recommended for version control)         |


















## ✨ Key Features of Poetry

Poetry is a powerful and modern tool for Python dependency management and packaging. Below are some of its standout features:

| Feature                         | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| ✅ **Unified Tooling**            | Handles dependency management, packaging, versioning, and publishing.        |
| ✅ **pyproject.toml Support**     | Uses the modern Python standard for project metadata.                        |
| ✅ **Dependency Resolution**      | Solves and locks dependencies using `poetry.lock`.                          |
| ✅ **Virtual Environment Management** | Automatically creates and manages virtual environments per project. |
| ✅ **Version Management**         | Supports semantic versioning and constraints like `^`, `~`, etc.            |
| ✅ **Easy Publishing**            | Built-in support for publishing packages directly to PyPI.                  |
| ✅ **Intuitive CLI**              | Clean, user-friendly command-line interface for common tasks.               |




## Installation Guide

### 1. Install Poetry via curl

**Poetry** provides a quick and easy installation method using a script that downloads and installs the latest version of Poetry. To get started, follow these steps:

#### Step 1: Install Poetry

Open your terminal and run the following command to download and install Poetry using `curl`:

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

- The curl command fetches the installation script.

- python3 - executes the script, installing Poetry.

### What happens during installation:

 - Poetry will be installed in your user's home directory (typically ~/.local/bin).

 -  The installation will also ensure that Poetry is available on your system's PATH, which is necessary for it to be accessible from the command line.

### 2. Add Poetry to PATH

After installation, **Poetry** might not automatically be added to your system's `PATH` (depending on your operating system). To make sure you can run **Poetry** from anywhere in your terminal, you may need to add it manually.

#### For Linux or macOS:
By default, **Poetry** is installed in `~/.local/bin`.

To add it to your `PATH`, follow these steps:

1. Open your terminal.
2. Edit your shell's configuration file. Depending on your shell, this could be `.bashrc`, `.zshrc`, or `.profile`. For example, to edit `.bashrc`, run:

   ```bash
   nano ~/.bashrc
   ```

3. Add the following line at the end of the file:

   ```bash
   export PATH="$HOME/.local/bin:$PATH"
   ```

 4. Reload your shell configuration by running:

    ```bash
    source ~/.bashrc   # or source ~/.zshrc, depending on your shell
    ```
This will ensure that Poetry is available globally on your system, allowing you to run it from any terminal window.

For **Windows:**

1. Find the Poetry installation directory. By default, it should be installed in %APPDATA%\Python\Scripts.

2. Add it to the system PATH:

    - Open System Properties (Windows key + Pause/Break → Advanced system settings → Environment Variables).

    -  Under System variables, find the Path variable, and click Edit.

    - Click New and add the path to the Poetry installation directory.

    - Click OK to apply the changes.

### 3. Check Poetry Version

Once **Poetry** is installed and added to your system's `PATH`, you can verify that the installation was successful by running the following command in your terminal:

```bash
poetry --version
```
this will display the installed version of Poetry, confirming that it is installed correctly.

**Example output:**

```bash
Poetry version 1.9.0

```

If you see the version number, it means Poetry is installed and ready to use!



# 📘 Basic Usage

Once Poetry is installed and working, you can start using it to manage your Python projects with a clean and modern workflow.

**🆕 1. Create a New Project**

To start a brand-new Python project with Poetry:

```bash
poetry new project_name
```
This command creates a fully-structured project directory with:

```bash
project_name/
├── project_name/
│   └── __init__.py
├── tests/
│   └── __init__.py
│   └── test_project_name.py
├── pyproject.toml
├── README.rst
```

- project_name/: The main package/module.

- tests/: Test directory (with a starter test file).

- pyproject.toml: Configuration file for dependencies, metadata, etc.

**➕ 2. Add, Install, and Remove Dependencies**

Poetry simplifies dependency management with just a few commands.

**✅ Add a dependency:**

```bash
poetry add requests
```

- Adds requests to the project.

- Updates pyproject.toml and poetry.lock.

To install a dev-only dependency (e.g., pytest for testing):

```bash
poetry add --dev pytest
```

**📦 Install dependencies:**

```bash
poetry install
```

- Installs all dependencies listed in pyproject.toml, using the exact versions in poetry.lock.

- Also sets up the virtual environment automatically.

**❌ Remove a dependency:**

```bash
poetry remove requests
```

- Removes it from pyproject.toml and uninstalls it from the virtual environment.

**🧪 3. Using the Virtual Environment**

Poetry creates and manages its own virtual environment behind the scenes, but you can interact with it easily.

**🚀 Activate the virtual environment:**

```bash
poetry shell

```

- Starts a new shell session inside the Poetry-managed virtual environment.

- Now you can run Python or other commands as if the environment were activated.

To exit, just run:

```bash
exit

```

**⚙️ Run a command inside the environment (without activating it):**

```bash
poetry run python script.py

```

- Runs script.py using the project's virtual environment.


**📦 4. Build the Package**

When you're ready to package your project:

```bash
poetry build

```

This command creates distribution files in the dist/ folder:

```bash
dist/
├── project_name-0.1.0.tar.gz  # Source archive
└── project_name-0.1.0-py3-none-any.whl  # Wheel file

```





## 🔍 Comparison: Poetry vs pip + venv

| Feature                         | pip + venv                                   | Poetry                                  |
|----------------------------------|-----------------------------------------------|------------------------------------------|
| **Dependency Installation**       | ✅ Yes                                       | ✅ Yes                                    |
| **Virtual Environment Creation** | ✅ Yes (`python -m venv`)                    | ✅ Yes (automatic)                        |
| **Lock File Generation**         | ❌ No (`requirements.txt` is static)         | ✅ Yes (`poetry.lock`)                    |
| **Dependency Resolution**        | ❌ Manual or via `pip-tools`                 | ✅ Automatic                              |
| **Project Metadata**             | `setup.py`, `requirements.txt`, `MANIFEST.in` | ✅ All in `pyproject.toml`              |
| **Dev vs Main Dependencies**     | ❌ No distinction                             | ✅ Clear separation                       |
| **Versioning & Publishing**      | Requires `setuptools`, `twine`, etc.         | ✅ Built-in                               |
| **Simplicity**                   | ❌ More moving parts                          | ✅ All-in-one tool                        |



## 🧠 Best Practices

- ✅ **Use Poetry for new projects** to benefit from its streamlined workflow.
- 📄 **Use `pyproject.toml` as the single source of truth** for dependencies, metadata, and configuration.
- 🔒 **Rely on `poetry.lock`** to ensure consistent and reproducible environments across your team.
- 🚫 **Avoid mixing `pip` and `poetry`** in the same project to prevent conflicts and environment issues.


## 🛠️ Troubleshooting

| Issue / Error                                 | Possible Cause                                             | Solution                                                                 |
|-----------------------------------------------|------------------------------------------------------------|--------------------------------------------------------------------------|
| `poetry: command not found`                   | Poetry is not in your system's `PATH`                      | Add Poetry’s bin directory to your `PATH` manually (see steps above)     |
| `Permission denied` during install            | Insufficient permissions                                   | Try running the install command with elevated privileges (`sudo`)       |
| Wrong Python version detected                 | Poetry uses system's default Python version                | Use `poetry env use python3.x` to set the correct version                |
| Dependencies not installing                   | Network issues or outdated lock file                       | Run `poetry lock --no-update` or check your internet connection          |
| Virtual environment not being created         | venv module might be missing or disabled                   | Ensure Python's `venv` module is installed and accessible                |
| Poetry installed but still not recognized     | Terminal session not refreshed                             | Restart terminal or run `source ~/.bashrc` / `source ~/.zshrc` etc.      |

## 📧 Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|


## 📚 Reference

| Link | Description |
|------|-------------|
| [https://python-poetry.org/docs/](https://python-poetry.org/docs/) | Documentation followed for this link |



