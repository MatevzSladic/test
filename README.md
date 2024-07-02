# WSl setup for XHS
This is a guide to setup your WSL workspace for work with SIRIUS-XHS devices. 
1. [INSTALLING WSL AND UBUNTU 20.04](#part-1-installing-wsl-and-ubuntu-2004)
2. [INSTALLING VISUAL STUDIO CODE](#part-2-installing-visual-studio-code)
3. [SETUP FOR XHS](#part-3-setup-for-siriusxhs-development)

## Part 1: Installing WSL and UBUNTU 20.04

### **1st option:**
S1. Open CMD as admin or Powershell and run 
```console
$ wsl --install --distribution Ubuntu-20.04
```

S2. restart your PC,

S3. wait for Ubuntu installation,

S4. set username and password (Username allows lowercase [a-z], underscore '_' and dash '-').

### **2nd option:**

**IF WSL ISN'T INSTALLED**

S1. Open CMD as admin or Powershell and run 
```console
$ wsl --install
```

S2. restart your PC

**IF WSL IS ALREADY INSTALLED**

S1. Open Microsoft Store,

S2. search for "Ubuntu 20.04 LTS",

[![Microsoft Store Ubuntu Download](./SetupScripts/MicrosoftStoreUbunut.png "Microsoft Store Ubuntu Download")](https://www.microsoft.com/store/productId/9MTTCL66CPXJ?ocid=pdpshare)

*Ubuntu 20.04 LTS in Microsoft Store*

S3. click on Get and wait untill the download is finished,

S4. click on Open and wait for the instalation,

S5. set username and password (Username allows lowercase [a-z], underscore '_' and dash '-').

## Part 2: Installing Visual Studio Code

S1. Download the 
<a href="https://go.microsoft.com/fwlink/?LinkID=534107" class="external-link" target="_blank">Visual Studio Code installer</a>
for Windows

S2. Once it is downloaded, run the installer (VSCodeUserSetup-{version}.exe).

> **Tip:** Setup will add Visual Studio Code to your %PATH%, so from the console you can type 'code .' to open VS Code on that folder. You will need to restart your console after the installation for the change to the %PATH% environmental variable to take effect.

**Make sure to keep the box saying "Add to PATH" checked!**

S3. Open PowerShell on Windows and run the following command
```console
$ code --install-extension ms-vscode-remote.remote-wsl
```

## Part 3: Setup for SiriusXHS development

### **SSH key setup:**

Run the following command to generate an SSH key. The command will gereate a key and outprint it in the console. After that just copy it and add it to the list of SSH keys in your GitLab account.  
```sh
$ cd ~ && sudo apt update && sudo apt upgrade -y && sudo apt install git && sudo apt install git-lfs && ssh-keygen && ssh-agent -s && sudo chmod 600 ~/.ssh/id_rsa && sudo chmod 600 ~/.ssh/id_rsa.pub && clear && cat ~/.ssh/id_rsa.pub
```

### **Cloning the SiriusXHS repository:**

After setting up the SSH key in your GitLab account Run the following command to clone the SiriusXHS repository to your home directory. **THIS MAY TAKE SOME TIME!**
```console
$ cd ~ && mkdir DSWorkspace && cd DSWorkspace && git lfs clone --recurse-submodules ssh://git@gitlab.dewesoft.com:2345/Devices/firmware/RT/SiriusXhs.git && cd ~
```

### **Running the setup script:**

After cloning the repository make sure you are located in your home directory. When you are, run the following command to start the execution of the setup script.
```console
$ cd ~ && chmod +x ./DSWorkspace/SiriusXhs/SetupScripts/Setup.sh && ./DSWorkspace/SiriusXhs/SetupScripts/Setup.sh
```

The script will ask you for your password and then it will install all the necessary packages and dependencies.

**THIS WILL TAKE SOME TIME**

You should follow the instructions given by the script and restart the WSL terminal after the script is done with the setup.
