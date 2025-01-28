# How to Set Up Project-Specific Library Imports in IPython

Follow these steps to configure IPython to pre-import specific libraries for a project:

## 1. Create a Startup Directory

In your project directory, create a folder for the startup script:

```bash
mkdir -p .ipython_startup
```

## 2. Add the Import Script

Create a Python script with the libraries you want to pre-import:

```bash
echo "import numpy as np\nimport pandas as pd" > .ipython_startup/imports.py
```

## 3. Create a Wrapper Script

Create a script to launch IPython with the custom imports:

```bash
echo "ipython --InteractiveShellApp.exec_files='[\"./.ipython_startup/imports.py\"]'" > ipython_local
chmod +x ipython_local
```

## 4. Run IPython with the Custom Setup

Use the wrapper script to start IPython in the current project directory:

```bash
./ipython_local
```

## 5. Share with Others

Share these steps or copy the `.ipython_startup` folder and `ipython_local` script into your coworkers' project directories.
This setup ensures the custom imports are specific to your project and won’t affect other IPython sessions.
