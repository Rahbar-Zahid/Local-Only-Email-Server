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

## Install Ubuntu
Now you can install Ubuntu from the Windows Store or via the command line.

### Via Microsoft Store
Search Ubuntu in the Microsoft store and install it.
You can install any specific version as well (like in my case I installed the 24.04 LTS version).

<img src="https://github.com/user-attachments/assets/31ed144f-4162-4cb7-806d-fef58943091c" alt="Ubuntu in Store" width ="50%" height="50%">

Just make sure to install the one provided by Canonical Group Ltd.
Now, open it for it to be able to install and register in Windows. When asked for a Unix username and password use whichever username and password you want.

### Via Command Line in Powershell(Administrator)
To view all available distros that can be installed, enter the command

`wsl --list --online`

<img src="https://github.com/user-attachments/assets/b801faa4-6001-4e8b-9d09-0f0e10c854e7" alt="List of Linux Distros in powershell" width="50%" height="50%">

To install your required distro in our case Ubuntu-24.04

`wsl --install -d Ubuntu-24.04`

You can replace <Ubuntu24.04> with whatever distribution of Linux you want to use.
When asked for a Unix username and password use whichever username and password you want.
Note: use lowercase letters
You can also use the following YouTube video for a more visual step-by-step guide.

[Ubuntu On WSL](https://youtu.be/7Sym3uL6YWo?si=1HF1zHWLwNf9XjQW)

Next, check the state of your wsl type 

`wsl -l -v`

<img src="https://github.com/user-attachments/assets/ebb14197-cfff-4f4b-99cb-11d88a04f7c0" alt="Installed Distros and WSL Version Running" width="50%" height="50%">

## Launch Ubuntu
To launch Ubuntu, either search ___Ubuntu 24.04 LTS___ in the Start Menu.

<img src="https://github.com/user-attachments/assets/816b4ed6-2215-4d36-9937-43cba551a4c7" alt ="Search Ubuntu 24.04 LTS" width="50%" height="50%">

Or enter the following command in Powershell.

`wsl -d Ubuntu-24.04`

<img src="https://github.com/user-attachments/assets/215ad799-0b16-4605-a258-4ea825f3cea2" alt = "Launching Ubuntu via powershell" width="50%" height="50%">


## Update Ubuntu

In the terminal enter the following commands one by one. Enter the password for authentication.

`sudo apt update`
<img src="https://github.com/user-attachments/assets/a8b29455-cfef-4d34-ab69-0388be00bbd6" alt= "sudo apt update" width="50%" height="50%">

`sudo apt upgrade`
<img src="https://github.com/user-attachments/assets/c35591cd-2af1-4d99-8a23-2621eaa26634" alt="sudo apt upgrade" width="50%" height="50%">


Note: if the update fails, try configuring the DNS within your Ubuntu as mentioned below.

### Configuring DNS
In the terminal, enter

`sudo nano /etc/resolv.conf`

and replace the nameserver with either 1.1.1.1 or 8.8.8.8 in the nano editor. Then press Ctrl+S to save and then Ctrl+X to close the nano editor.

Next, enter

`sudo nano /etc/wsl.conf`

and paste the following in the nano editor.

`[network]
generateResolvConf = false
`

Try updating again, it should come through.

## Enable systemd
To enable systems, first open wsl.conf via the following terminal command

`sudo nano /etc/wsl.conf`

and paste following

`
[boot]
systemd=true
`

<img src ="https://github.com/user-attachments/assets/fd246961-246a-4ca1-8c6d-95689c82b706" alt="wsl.conf" width="40%" height="50%">


This allows multiple features and packages in your Ubuntu system to be used in the future.
Update Ubuntu once more.
Note: if the update fails again, go through the Configuring DNS steps again and you should be good.

## Install and set up Postfix and Dovecot

