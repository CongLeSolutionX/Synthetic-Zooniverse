---
created: 2025-03-10 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# pyenv - A step-by-step installation guide
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

**`pyenv`** is an excellent tool for managing multiple Python versions and creating isolated virtual environments on your system. Below is a comprehensive, step-by-step guide to installing `pyenv`, setting up Python 3.9, and creating a virtual environment using `pyenv` on macOS.

---

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Installing `pyenv`](#installing-pyenv)
3. [Configuring Your Shell for `pyenv`](#configuring-your-shell-for-pyenv)
4. [Installing Python 3.9 with `pyenv`](#installing-python-39-with-pyenv)
5. [Verifying the Python Installation](#verifying-the-python-installation)
6. [Installing `pyenv-virtualenv`](#installing-pyenv-virtualenv)
7. [Creating a Virtual Environment with Python 3.9](#creating-a-virtual-environment-with-python-39)
8. [Activating and Deactivating the Virtual Environment](#activating-and-deactivating-the-virtual-environment)
9. [Setting the Local Python Version for a Project](#setting-the-local-python-version-for-a-project)
10. [Additional Tips and Troubleshooting](#additional-tips-and-troubleshooting)
11. [Conclusion](#conclusion)

---

## 1. Prerequisites

Before proceeding, ensure you have the following:

- **Homebrew Installed**: Homebrew is a package manager for macOS, which simplifies the installation of software like `pyenv`.

  If you don't have Homebrew installed, you can install it by running the following command in your terminal:

  ```bash
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```

- **Command Line Tools for Xcode**: These are necessary for building Python versions from source.

  Install them by running:

  ```bash
  xcode-select --install
  ```

  Follow the on-screen instructions to complete the installation.

---

## **2. Installing `pyenv`**

There are multiple ways to install `pyenv`. The recommended method on macOS is via Homebrew.

### **Step 1: Update Homebrew**

First, ensure that Homebrew is up-to-date:

```bash
brew update
```

### **Step 2: Install `pyenv`**

Install `pyenv` using Homebrew:

```bash
brew install pyenv
```

### **Step 3: (Optional) Install `pyenv-virtualenv`**

While optional, `pyenv-virtualenv` simplifies the creation and management of virtual environments.

```bash
brew install pyenv-virtualenv
```

---

## **3. Configuring Your Shell for `pyenv`**

After installing `pyenv`, you need to configure your shell to initialize `pyenv` automatically.

### **Step 1: Identify Your Shell**

Determine which shell you are using (e.g., `bash`, `zsh`).

```bash
echo $SHELL
```

macOS Catalina and later versions use `zsh` by default. If you're using an older macOS version, you might be using `bash`.

### **Step 2: Update Shell Configuration File**

Depending on your shell, you'll need to update either `.zshrc` or `.bash_profile`.

#### **For `zsh` Users:**

1. Open `.zshrc` in your preferred text editor. For example:

   ```bash
   nano ~/.zshrc
   ```

2. Add the following lines at the end of the file:

   ```bash
   # Pyenv Configuration
   export PYENV_ROOT="$HOME/.pyenv"
   export PATH="$PYENV_ROOT/bin:$PATH"
   eval "$(pyenv init --path)"
   eval "$(pyenv init -)"
   eval "$(pyenv virtualenv-init -)"  # Only if pyenv-virtualenv is installed
   ```

3. Save and exit the editor (for `nano`, press `CTRL + X`, then `Y`, and `Enter`).

#### **For `bash` Users:**

1. Open `.bash_profile` or `.bashrc` in your preferred text editor. For example:

   ```bash
   nano ~/.bash_profile
   ```

2. Add the following lines at the end of the file:

   ```bash
   # Pyenv Configuration
   export PYENV_ROOT="$HOME/.pyenv"
   export PATH="$PYENV_ROOT/bin:$PATH"
   eval "$(pyenv init --path)"
   eval "$(pyenv init -)"
   eval "$(pyenv virtualenv-init -)"  # Only if pyenv-virtualenv is installed
   ```

3. Save and exit the editor.

### **Step 3: Reload Shell Configuration**

Apply the changes by reloading your shell configuration:

```bash
source ~/.zshrc  # For zsh users
# or
source ~/.bash_profile  # For bash users
```

---

## **4. Installing Python 3.9 with `pyenv`**

With `pyenv` installed and configured, you can now install Python 3.9.

### **Step 1: Check Available Python Versions**

List all available Python versions that `pyenv` can install:

```bash
pyenv install --list
```

Look for the desired 3.9.x version (e.g., `3.9.13`).

### **Step 2: Install Python 3.9**

Install a specific Python 3.9 version (replace `3.9.13` with your desired minor version if needed):

```bash
pyenv install 3.9.13
```

**Note:** The installation might take several minutes as `pyenv` compiles Python from source. Ensure you have a stable internet connection.

### **Troubleshooting Installation Errors**

If you encounter errors during installation, you might be missing some dependencies. Install common dependencies via Homebrew:

```bash
brew install openssl readline sqlite3 xz zlib tcl-tk
```

After installing dependencies, retry installing Python 3.9:

```bash
pyenv install 3.9.13
```

---

## **5. Verifying the Python Installation**

After installation, verify that Python 3.9 is correctly installed.

### **Step 1: List Installed Python Versions**

```bash
pyenv versions
```

You should see an entry like:

```
* system (set by /Users/yourusername/.pyenv/version)
  3.9.13
```

### **Step 2: Set Global Python Version (Optional)**

If you want Python 3.9 to be the default Python version globally (across all projects), set it as the global version:

```bash
pyenv global 3.9.13
```

Verify the change:

```bash
python --version
# or
python3 --version
```

The output should be:

```
Python 3.9.13
```

**Note:** Setting a global Python version is optional. You can set Python versions per project without affecting the global setting.

---

## **6. Installing `pyenv-virtualenv`**

`pyenv-virtualenv` is a plugin that seamlessly integrates `pyenv` with Python virtual environments.

### **Step 1: Install `pyenv-virtualenv`**

If you haven't installed `pyenv-virtualenv` yet, you can install it via Homebrew:

```bash
brew install pyenv-virtualenv
```

### **Step 2: Verify Installation**

Ensure that `pyenv-virtualenv` is installed correctly:

```bash
pyenv virtualenv --version
```

You should see the version number, e.g., `pyenv-virtualenv 1.1.8`.

### **Step 3: Reconfigure Shell (If Necessary)**

If you installed `pyenv-virtualenv` after configuring your shell, ensure that the following line exists in your shell configuration file (`.zshrc` or `.bash_profile`):

```bash
eval "$(pyenv virtualenv-init -)"
```

If not, add it, then reload the shell configuration:

```bash
source ~/.zshrc  # For zsh users
# or
source ~/.bash_profile  # For bash users
```

---

## **7. Creating a Virtual Environment with Python 3.9**

Now, create a virtual environment using Python 3.9.

### **Step 1: Choose a Name for Your Virtual Environment**

Example: `myenv-3.9.13`

### **Step 2: Create the Virtual Environment**

```bash
pyenv virtualenv 3.9.13 myenv-3.9.13
```

### **Step 3: List All Virtual Environments**

To see all existing virtual environments:

```bash
pyenv virtualenvs
```

You should see an entry like:

```
  myenv-3.9.13 (created from /Users/yourusername/.pyenv/versions/3.9.13)
```

---

## **8. Activating and Deactivating the Virtual Environment**

### **Option 1: Using `pyenv activate` and `pyenv deactivate`**

#### **Activate the Virtual Environment**

```bash
pyenv activate myenv-3.9.13
```

After activation, your shell prompt might change to indicate the active environment, e.g., `(myenv-3.9.13) your-macbook:~ yourusername$`

#### **Deactivate the Virtual Environment**

```bash
pyenv deactivate
```

### **Option 2: Using `pyenv shell`**

Alternatively, you can set the virtual environment for the current shell session:

```bash
pyenv shell myenv-3.9.13
```

To unset:

```bash
pyenv shell --unset
```

### **Option 3: Automatically Activate in a Project Directory**

If you want the virtual environment to activate automatically when you navigate to a specific project directory:

1. **Navigate to Your Project Directory:**

   ```bash
   cd /path/to/your/project
   ```

2. **Set the Local Python Version:**

   ```bash
   pyenv local myenv-3.9.13
   ```

   This command creates a `.python-version` file in the current directory with the virtual environment name. When you `cd` into this directory, `pyenv` automatically activates the virtual environment.

---

## **9. Setting the Local Python Version for a Project**

To ensure that a specific project uses Python 3.9 via the virtual environment, you can set it locally within the project directory.

### **Step 1: Navigate to Your Project Directory**

```bash
cd /path/to/your/project
```

### **Step 2: Set the Local Python Version**

Use `pyenv` to set the local version to your virtual environment:

```bash
pyenv local myenv-3.9.13
```

This command writes `myenv-3.9.13` to a `.python-version` file in the project directory.

### **Step 3: Verify the Local Python Version**

```bash
python --version
```

You should see:

```
Python 3.9.13
```

Whenever you navigate to this project directory, `pyenv` automatically activates `myenv-3.9.13`.

---

## **10. Additional Tips and Troubleshooting**

### **1. Listing All Installed Python Versions and Virtual Environments**

```bash
pyenv versions
```

### **2. Removing a Virtual Environment**

If you want to delete a virtual environment:

```bash
pyenv uninstall myenv-3.9.13
```

### **3. Updating `pyenv`**

Keep `pyenv` and its plugins up-to-date to benefit from the latest features and fixes.

```bash
brew update
brew upgrade pyenv
brew upgrade pyenv-virtualenv  # If installed
```

### **4. Installing Additional Python Versions**

To install another Python version, repeat the installation steps:

```bash
pyenv install 3.10.4
pyenv virtualenv 3.10.4 myenv-3.10.4
```

### **5. Switching Between Python Versions**

You can switch between Python versions or virtual environments globally, locally, or per shell.

- **Set Global Python Version:**

  ```bash
  pyenv global 3.9.13
  ```

- **Set Local Python Version (per project):**

  ```bash
  pyenv local 3.10.4
  ```

- **Set Shell Python Version (current session):**

  ```bash
  pyenv shell myenv-3.10.4
  ```

### **6. Ensuring Dependencies for Building Python Versions**

For macOS, ensure you have necessary dependencies installed:

```bash
brew install openssl readline sqlite3 xz zlib tcl-tk
```

If you encounter build errors, these dependencies are often the cause.

### **7. Using `.python-version` Files**

Be mindful of `.python-version` files in your directory hierarchy. These files determine the Python version for a directory and its subdirectories.

- **Check Current `.python-version`:**

  ```bash
  cat .python-version
  ```

- **Remove `.python-version` File:**

  ```bash
  rm .python-version
  ```

### **8. Displaying Current Python Version**

To see which Python version is currently active:

```bash
pyenv version
```

### **9. Rehashing `pyenv`**

After installing new executables (like new versions or virtual environments), run:

```bash
pyenv rehash
```

This updates `pyenv`'s shims to recognize the new executables.

---

## **11. Conclusion**

Using `pyenv` and `pyenv-virtualenv` provides a powerful and flexible way to manage multiple Python versions and create isolated virtual environments on your macOS system. By following the steps outlined above, you can:

- **Install and Manage Multiple Python Versions**: Easily switch between different Python versions for different projects.

- **Create Isolated Virtual Environments**: Ensure that project dependencies are isolated, preventing conflicts and promoting cleaner development workflows.

- **Maintain Flexibility and Control**: Fine-tune Python environments on a per-project basis, enhancing both development efficiency and system stability.

---

## **Summary of Commands**

For quick reference, here's a summary of the key commands used in this guide:

```bash
# Install pyenv
brew update
brew install pyenv
brew install pyenv-virtualenv  # Optional

# Configure shell (add to ~/.zshrc or ~/.bash_profile)
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"  # If pyenv-virtualenv is installed

# Reload shell configuration
source ~/.zshrc  # For zsh
# or
source ~/.bash_profile  # For bash

# Install Python 3.9.x
pyenv install 3.9.13

# Set global Python version (optional)
pyenv global 3.9.13

# Install virtualenv plugin
brew install pyenv-virtualenv

# Create a virtual environment
pyenv virtualenv 3.9.13 myenv-3.9.13

# Activate the virtual environment
pyenv activate myenv-3.9.13

# Deactivate the virtual environment
pyenv deactivate

# Set local Python version for a project
cd /path/to/your/project
pyenv local myenv-3.9.13
```

---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---