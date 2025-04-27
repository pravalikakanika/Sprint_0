![image](https://github.com/user-attachments/assets/6c813200-6ff4-4ad3-a193-7b2d8cde7718)



| Author        | Date       | Version | Review Level   | Reviewer Name        |
|---------------|------------|---------|----------------|----------------------|
| pravalika Kanikarapu  | April 20   | v1.1    | Pre-Reviewer   | Priyanshu            |
| pravalika Kanikarapu  | April 24   | v2.1    | L0             | Khushi Malothra      |
| pravalika Kanikarapu  |            |         | L1             | Rishabh Sharma       |
| pravalika Kanikarapu  |            |         | L2             | piyush Upadhyay      |



#  Table of Contents

- [ Introduction](#Introduction)

- [ What is poetry?](#what-is-poetry)

- [ Why Use Poetry?](#why-use-poetry)

- [ Its Role in Modern Python Project Management](#its-role-in-modern-python-project-management)


- [Purpose of Using Poetry](#purpose-of-using-poetry)

- [ Key Features of Poetry](#key-features-of-poetry)

- [Installation of Poetry](#installation-of-poetry)
   
- [ Comparison: Poetry vs pip + venv](#comparison-poetry-vs-pip--venv)

- [Conclusion](#Conclusion).

- [ Contact Information](#contact-information)

- [ Reference](#reference)









# Introduction 

This document serves as a comprehensive guide to understanding, installing, and effectively using Poetry in your Python projects.This guide will help you leverage Poetry’s powerful features—from dependency management to packaging and publishing—using the modern pyproject.toml standard.



# What is poetry?

###  Definition

**Poetry** is a Python dependency management and packaging tool that simplifies the way developers build, manage, and distribute Python projects. It provides a standardized and streamlined workflow for everything from dependency installation to package publishing.


## Replaces Traditional Tools Like:

| Traditional Tool     | Poetry Replacement / Feature                                           |
|----------------------|------------------------------------------------------------------------|
| **pip**              | `poetry add`, `poetry install` handles installs, version pinning       |
| **venv / virtualenv**| Poetry automatically manages virtual environments                      |
| **setuptools**       | Handled via `pyproject.toml` (build metadata), no manual setup needed |
| **requirements.txt** | Uses `pyproject.toml` and `poetry.lock` instead                        |
| **twine**            | Replaced with `poetry publish` for publishing packages                 |


# Why Use Poetry?

###  Simplifies Dependency & Project Management

Poetry replaces manual files like requirements.txt and setup.py with a single pyproject.toml.
Just run poetry add <package> to manage dependencies—Poetry updates the files for you and creates a poetry.lock for consistent installs.

##   Reproducible Builds
The poetry.lock file locks exact versions of dependencies, ensuring your project runs the same across all environments.

##   Built-in Virtual Environment Handling

Poetry automatically creates and manages virtual environments per project—no need for pip, venv, or virtualenv.



# Purpose of Using Poetry

| Goal  | Description |
|--------|-------------|
| 1      | **Replaces multiple tools** like `pip`, `venv`, `setup.py`, `requirements.txt`, and `twine` with one unified interface. |
| 2      | **Manages dependencies** declaratively and reproducibly using `pyproject.toml`, making it easier to maintain consistent environments. |
| 3      | **Automatically handles virtual environments** for each project, eliminating the need for manual `venv` creation and activation. |
| 4      | **Simplifies publishing** Python packages by enabling direct uploads to PyPI with minimal configuration. |
| 5      | **Uses `pyproject.toml`** as a centralized configuration file that follows modern Python packaging standards. |




# Key Features of Poetry

Poetry is a powerful and modern tool for Python dependency management and packaging. Below are some of its standout features:

| Feature                         | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
|  **Unified Tooling**            | Handles dependency management, packaging, versioning, and publishing.        |
|  **pyproject.toml Support**     | Uses the modern Python standard for project metadata.                        |
|  **Dependency Resolution**      | Solves and locks dependencies using `poetry.lock`.                          |
|  **Virtual Environment Management** | Automatically creates and manages virtual environments per project. |
|  **Version Management**         | Supports semantic versioning and constraints like `^`, `~`, etc.            |
|  **Easy Publishing**            | Built-in support for publishing packages directly to PyPI.                  |
|  **Intuitive CLI**              | Clean, user-friendly command-line interface for common tasks.               |


##  Installation of Poetry 

For Installation Of The Poetry Follow this Link


[Poetry Installation](https://github.com/Cloud-NInja-snaatak/Documentation/blob/rajeev_scrum18/commonstack/applications/python/poetry/sop.md)


# Comparison: Poetry vs pip & venv

| Feature / Tool              | pip (Package Installer)                                                                 | venv (Virtual Environment)                                                              | Poetry (All-in-One Tool)                                                                 |
|----------------------------|------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| **Purpose**                | Installs Python packages from PyPI or other indexes.                                     | Creates isolated environments to prevent dependency conflicts across projects.          | Manages dependencies, environments, versioning, and publishing in one tool.              |
| **Package Management**     | Yes – installs packages using `pip install package_name`.                                | No – does not manage or install packages.                                                | Yes – uses `poetry add` to install and track dependencies.                               |
| **Environment Isolation**  | No – uses the global Python environment unless inside a venv.                            | Yes – creates a clean, isolated environment per project.                                | Yes – automatically creates and uses per-project virtual environments.                   |
| **Lock File**              | No – uses `requirements.txt` which may not pin all transitive dependencies.              | No – does not handle dependency files.                                                   | Yes – uses `poetry.lock` to ensure consistent builds and versions across machines.       |
| **Handles Dev Dependencies** | No – all packages must be manually tracked.                                             | No – does not handle packages.                                                           | Yes – allows separation of dev and runtime dependencies using `--dev` flag.              |
| **Project Metadata**       | Requires multiple files like `setup.py`, `MANIFEST.in`, and `requirements.txt`.          | No – not related to project metadata.                                                    | Yes – all metadata is declared in `pyproject.toml`.                                      |
| **Build & Publish Package**| Requires `setuptools`, `wheel`, and `twine` for packaging and publishing to PyPI.        | No – not used for packaging.                                                             | Yes – supports `poetry build` and `poetry publish` directly from the CLI.                |
| **Ease of Use**            | Medium – needs manual setup of virtual environments and multiple tools.                  | Medium – handles only one part of the workflow; must be combined with pip.               | Easy – unified CLI handles setup, dependencies, environments, and publishing.            |
| **Common Usage**           | Used to install packages into a virtual environment manually created with `venv`.        | Used to isolate environments and then combined with pip for package installs.            | Used for full-cycle project management, from project creation to publishing.             |





# Conclusion 

Poetry represents a significant step forward in simplifying and standardizing Python project management.With its use of the pyproject.toml file as a single source of truth, automatic virtual environment creation, reliable dependency resolution through poetry.lock, and built-in tools for publishing to PyPI, Poetry empowers developers to focus more on building and less on configuration.

# Contact Information


| Name       | Email Address                |
|------------|------------------------------|
| Pravalika  | kanikarapu.pravalika.snaatak@mygurukulam.co|


# Reference

| Link | Description |
|------|-------------|
| [https://python-poetry.org/docs/](https://python-poetry.org/docs/) | Documentation followed for this link |


