
![image](https://github.com/user-attachments/assets/c9a06dd3-3744-4660-8f6b-3c46763af5b9)


## 📂 Document Info

| Author   | Created on | Version  | Last Edited On | Internal-Reviewer | L0-Reviewer  | L1-Reviewer | L2-Reviewer  |
|----------|------------|----------|----------------|-------------------|--------------|-------------|--------------|
| kanika  | 18-04-25   | version 2| 18-04-25       | priyanshu     | priyanka Balidkar| Rishabh sharma | Piyush upadyay |



# Purpose of `react-setup.sh`

The `react-setup.sh` script is designed to:

| 🔧 **Feature**               | 📌 **Purpose**                                                                                           |
|-----------------------------|---------------------------------------------------------------------------------------------------------|
| ✅ **Automate React Setup**  | Quickly set up a new or existing React project using a single Bash script.                                |
| 🔁 **Support Multiple React Versions** | Easily install or upgrade to any version of React (e.g. 17.0.2, 18.2.0, latest).                          |
| 🛠️ **Install Node.js (if missing)** | Checks if Node.js is installed and optionally installs it (on Linux/macOS).                             |
| 🧱 **Initialize Project**    | Automatically creates a React project using `create-react-app` if `package.json` doesn't exist.           |
| 🧪 **Use npm or yarn**       | Lets you choose your preferred package manager (`npm` or `yarn`).                                        |
| ♻️ **Re-run for Upgrades**   | Can be reused any time to upgrade React versions in an existing project.                                |
| 💻 **Cross-platform**        | Works on Linux, macOS, and Windows (via Git Bash or WSL).                                                |
| 💼 **DevOps Friendly**       | Useful in CI/CD pipelines or setting up dev environments automatically.                                  |







## 🧰 Prerequisite Tools

Before running or setting up the project, make sure you have the following tools installed:

| 🛠️ Tool              | 🔍 Purpose                             | 💡 How to Check                | 📥 Install Instructions                                                                 |
|----------------------|-----------------------------------------|--------------------------------|------------------------------------------------------------------------------------------|
| **Bash**             | Runs the shell script                   | `bash --version`               | Default on Linux/macOS. On Windows, use Git Bash or [WSL](https://learn.microsoft.com/en-us/windows/wsl/install). [Install Git Bash](https://git-scm.com/downloads) |
| **Node.js (v14+ recommended, v18+ ideal)** | Required to run React apps        | `node -v`                      | [Download Node.js](https://nodejs.org/) or use `nvm`, `brew`, or your OS package manager |
| **npm**              | Installs packages like React            | `npm -v`                        | Comes bundled with Node.js                                                              |
| **npx**              | Runs CLI tools like `create-react-app` | `npx -v`                        | Included with npm `v5.2+`                                                                |
| **yarn** *(optional)*| Alternative package manager             | `yarn -v`                       | `npm install -g yarn` or [Install Yarn](https://classic.yarnpkg.com/en/docs/install)     |
| **create-react-app** | Bootstraps new React apps               | `create-react-app --version`   | Installed by the setup script or manually via `npm install -g create-react-app`         |
| **curl** or **wget** | Downloads Node.js setup scripts (Linux only) | `curl --version` or `wget --version` | `sudo apt install curl` (Linux) or `brew install curl` (macOS)                          |
| **Internet Access**  | Needed to download packages             | —                              | Required for all installations and updates                                               |

> ✅ Tip: You can use [nvm (Node Version Manager)](https://github.com/nvm-sh/nvm) to easily install and switch between different versions of Node.js.


# ✅ Bash Script: install-react.sh


```bash
#!/bin/bash

# Usage: ./install-react.sh my-app 18.2.0
# Or: ./install-react.sh my-app latest

APP_NAME=$1
REACT_VERSION=$2

if [ -z "$APP_NAME" ] || [ -z "$REACT_VERSION" ]; then
  echo "Usage: $0 <app-name> <react-version|latest>"
  exit 1
fi

# Create or navigate to app directory
if [ ! -d "$APP_NAME" ]; then
  echo "Creating project directory: $APP_NAME"
  mkdir "$APP_NAME"
fi

cd "$APP_NAME" || exit

# Initialize package.json if not present
if [ ! -f "package.json" ]; then
  echo "Initializing npm..."
  npm init -y
else
  echo "package.json found, skipping init."
fi

# Install specific React version
if [ "$REACT_VERSION" == "latest" ]; then
  echo "Installing latest React and ReactDOM..."
  npm install react react-dom
else
  echo "Installing React@$REACT_VERSION and ReactDOM@$REACT_VERSION..."
  npm install "react@$REACT_VERSION" "react-dom@$REACT_VERSION"
fi

# Optional: Check installation
echo "Installed React version:"
npx react --version 2>/dev/null || echo "Use 'npm list react' to see version"

# Final project structure
echo "Project '$APP_NAME' is ready with React@$REACT_VERSION."
```


