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
