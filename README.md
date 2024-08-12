# Local-Only-Email-Server
## Setup Environment 
We are running our Ubuntu on **WSL**. To setup on wsl follow the following wsl setup guide.
Before we start, make sure you have virtualization enabled in BIOS.
Enable _Virtualization_ and _WSL_ features. For that, in the Start Menu, Search ___Features on and off___.

<img src="https://github.com/user-attachments/assets/a720755c-1508-4ffa-a71f-2a638bc34ef0" alt="Search Features on and Off" width="55%" height="60%">


It will open Windows Features. In it find and enable ___Virtual Machine Platform___ and ___Windows subsystem for Linux___.

<img src="https://github.com/user-attachments/assets/55b6d2a0-7e10-4c9f-9df7-679bacd15399" alt="Windows Features on and off" width="45%" height="50%">


Press Ok and restart the PC. 

Afterwards, open Powershell as administrator and run the command

`wsl --install`

Make sure you have WSL2 installed.

`wsl --status`

##Install Ubuntu
Now you can install Ubuntu from the Windows Store or via the command line.

###Via Microsoft Store
Search Ubuntu in the Microsoft store and install it.
You can install any specific version as well (like in my case I installed the 24.04 LTS version).

<img src="https://github.com/user-attachments/assets/31ed144f-4162-4cb7-806d-fef58943091c" alt="Ubuntu in Store" width ="50%" height="50%">

Just make sure to install the one provided by Canonical Group Ltd.
Now, open it for it to be able to install and register in Windows. When asked for a Unix username and password use whichever username and password you want.

###Via Command Line in Powershell(Administrator)
To view all available distros that can be installed, enter command

`wsl --list --online`

<img src="![image](https://github.com/user-attachments/assets/b801faa4-6001-4e8b-9d09-0f0e10c854e7" alt="List of Linux Distros in powershell" width="50%" height="50%">

To install your required distro in our case Ubuntu-24.04

`wsl --install -d Ubuntu-24.04`

You can replace <Ubuntu24.04> with whatever distribution of Linux you want to use.
When asked for a Unix username and password use whichever username and password you want.
Note: use lowercase letters
You can also use the following YouTube video for a more visual step-by-step guide.

[Ubuntu On WSL](https://youtu.be/7Sym3uL6YWo?si=1HF1zHWLwNf9XjQW)

Next to check state of your wsl type 

`wsl -l -v`

<img src="https://github.com/user-attachments/assets/ebb14197-cfff-4f4b-99cb-11d88a04f7c0" alt="Installed Distros and WSL Version Running" width="50%" height="50%">
