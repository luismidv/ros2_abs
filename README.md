# Flexley Stack Load Perception - Setup Guide

Welcome to the Flexley Stack Load Perception project! This guide will help you set up the project on your machine.

## Prerequisites

Before you begin, ensure you have the following:
- Windows 10 or Windows 11 (for WSL support)
- Administrator access to your machine
- A text editor or IDE of your choice
- Internet connection for downloading dependencies

---

## Installation & Setup Instructions

### Step 1: Install Windows Subsystem for Linux (WSL)

WSL allows you to run a Linux environment directly on Windows without needing a virtual machine.

1. Open **PowerShell** as Administrator
2. Run the following command to install WSL 2 with Ubuntu:
   ```powershell
   wsl --install
   ```
3. Restart your computer when prompted
4. After restart, Ubuntu will automatically finish its installation
5. Create a username and password for your Linux environment
6. Verify the installation by opening PowerShell and running:
   ```powershell
   wsl --version
   ```

For more detailed instructions, refer to the [official Microsoft WSL documentation](https://learn.microsoft.com/en-us/windows/wsl/install).

---

### Step 2: Clone the Bitbucket Repository

1. Open your WSL terminal (Ubuntu)
2. Navigate to where you want to store the project:
   ```bash
   cd ~
   ```
3. Clone the Flexley Stack Load Perception repository:
   ```bash
   git clone https://bitbucket.org/astimr/flexley-stack-load-perception.git
   ```
4. Wait for the cloning process to complete

---

### Step 3: Navigate to the Repository Folder

1. Move into the cloned repository directory:
   ```bash
   cd flexley-stack-load-perception
   ```
2. Verify the contents:
   ```bash
   ls -la
   ```

---

### Step 4: Set Execution Permissions on the Setup Script

The setup script needs to be executable. Grant the necessary permissions:

```bash
sudo chmod a+rx setup_load_perception_amd64.sh
```

You will be prompted to enter your Linux password. This command:
- `sudo`: Runs the command with administrator privileges
- `chmod`: Changes file permissions
- `a+rx`: Adds read and execute permissions for all users

---

### Step 5: Run the Setup Script

Execute the setup script to install all dependencies and configure the environment:

```bash
./setup_load_perception_amd64.sh
```

This script will:
- Install required system dependencies
- Set up Python environment
- Configure Conda with necessary packages
- Create and activate the `load_perception` Conda environment

Wait for the script to complete. This may take several minutes depending on your internet connection and machine speed.

---

### Step 6: Conda Environment Activation

Once the script completes successfully, the `load_perception` Conda environment will be activated automatically. You should see `(load_perception)` at the beginning of your terminal prompt.

To manually activate this environment in future sessions, run:
```bash
conda activate load_perception
```

To deactivate the environment, run:
```bash
conda deactivate
```

---

### Step 7: Download and Extract Required Folders

1. Download the mmlab packages from the following link:
   [Download mmlab_loadperception](https://abb-my.sharepoint.com/:u:/r/personal/mohammad_kassem-zein_es_abb_com/Documents/Microsoft%20Teams%20Chat%20Files/mmlab_loadperception%201.zip?csf=1&web=1&e=gzk2Qd)

2. Move the downloaded `mmlab_loadperception_1.zip` file to your home directory:
   ```bash
   mv ~/Downloads/mmlab_loadperception_1.zip ~/
   ```
   *(Adjust the path based on where your browser saves downloads)*

3. Navigate to your home directory:
   ```bash
   cd ~
   ```

4. Unzip the downloaded file:
   ```bash
   unzip mmlab_loadperception_1.zip
   ```

5. Verify that the folders were extracted correctly:
   ```bash
   ls -la
   ```
   You should see two folders: `mmpose` and `mmdetection`

---

### Step 8: Install mmpose and mmdetection Packages

Make sure your Conda environment `load_perception` is activated (you should see `(load_perception)` in your terminal prompt).

#### Install mmpose:

1. Navigate to the mmpose folder:
   ```bash
   cd ~/mmpose
   ```

2. Install the package in development mode:
   ```bash
   pip install -v -e .
   ```
   This command:
   - `pip install`: Installs the package
   - `-v`: Verbose mode (shows detailed output)
   - `-e`: Installs in editable/development mode (useful for development)
   - `.`: Uses the current directory

3. Wait for the installation to complete

#### Install mmdetection:

1. Navigate to the mmdetection folder:
   ```bash
   cd ~/mmdetection
   ```

2. Install the package in development mode:
   ```bash
   pip install -v -e .
   ```

3. Wait for the installation to complete

---

## Verification

To verify that everything is set up correctly:

1. Activate the Conda environment:
   ```bash
   conda activate load_perception
   ```

2. Test the imports:
   ```bash
   python -c "import mmpose; import mmdetection; print('All packages imported successfully!')"
   ```

If no errors appear, your setup is complete!

---

## Troubleshooting

### Issue: Permission denied when running setup script
**Solution:** Ensure you ran `sudo chmod a+rx setup_load_perception_amd64.sh` correctly.

### Issue: WSL not installing
**Solution:** Make sure virtualization is enabled in your BIOS/UEFI settings.

### Issue: pip install fails
**Solution:** 
- Ensure the Conda environment is activated
- Try updating pip: `pip install --upgrade pip`
- Check your internet connection

### Issue: Git clone fails
**Solution:**
- Check your internet connection
- Verify the repository URL is correct
- Make sure you have Git installed in WSL: `sudo apt-get install git`

---

## Additional Resources

- [WSL Official Documentation](https://learn.microsoft.com/en-us/windows/wsl/)
- [Conda Documentation](https://docs.conda.io/)
- [MMPose Documentation](https://mmpose.readthedocs.io/)
- [MMDetection Documentation](https://mmdetection.readthedocs.io/)

---

## Support

If you encounter any issues during setup, please:
1. Check this README's troubleshooting section
2. Review the console output for error messages
3. Contact the project team for assistance

---

**Last Updated:** April 2026
