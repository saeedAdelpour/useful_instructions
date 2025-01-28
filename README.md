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


# Setup Cloudflare Warp
## Ubuntu
```bash
curl -fsSL https://pkg.cloudflareclient.com/pubkey.gpg | sudo gpg --yes --dearmor --output /usr/share/keyrings/cloudflare-warp-archive-keyring.gpg

### Add this repo to your apt repositories
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/cloudflare-warp-archive-keyring.gpg] https://pkg.cloudflareclient.com/ $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/cloudflare-client.list

### Install
sudo apt-get update && sudo apt-get install cloudflare-warp
```

## Debian
```bash
### Add cloudflare gpg key
curl -fsSL https://pkg.cloudflareclient.com/pubkey.gpg | sudo gpg --yes --dearmor --output /usr/share/keyrings/cloudflare-warp-archive-keyring.gpg

### Add this repo to your apt repositories
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/cloudflare-warp-archive-keyring.gpg] https://pkg.cloudflareclient.com/ $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/cloudflare-client.list

### Install
sudo apt-get update && sudo apt-get install cloudflare-warp
```

## RedHat/Centos
```bash
### Add cloudflare-warp.repo to /etc/yum.repos.d/
curl -fsSl https://pkg.cloudflareclient.com/cloudflare-warp-ascii.repo | sudo tee /etc/yum.repos.d/cloudflare-warp.repo

### Update repo
sudo yum update

### Install
sudo yum install cloudflare-warp
```

## commands

```
warp-cli registration new
warp-cli registration license
warp-cli mode proxy
warp-cli proxy port 4000 // or anything
warp-cli connect
```