# Local-Only-Email-Server
## Setup Environment 
We are running our Ubuntu on **WSL**. 
WSL is a feature in Windows that allows you to run a Linux environment directly on your Windows computer.

To setup wsl, follow the following wsl setup guide.
Before we start, make sure you have virtualization enabled in BIOS.
Enable _Virtualization_ and _WSL_ features. For that, in the Start Menu, Search ___Features on and off___.

<img src="https://github.com/user-attachments/assets/a720755c-1508-4ffa-a71f-2a638bc34ef0" alt="Search Features on and Off" width="55%" height="60%">


It will open Windows Features. In it find and enable ___Virtual Machine Platform___ and ___Windows subsystem for Linux___.

<img src="https://github.com/user-attachments/assets/55b6d2a0-7e10-4c9f-9df7-679bacd15399" alt="Windows Features on and off" width="45%" height="50%">


Press Ok and restart the PC. 

Afterwards, open Powershell as administrator and run the command

```
wsl --install
```

Make sure you have WSL2 installed.

```
wsl --status
```

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

```
wsl --list --online
```

<img src="https://github.com/user-attachments/assets/b801faa4-6001-4e8b-9d09-0f0e10c854e7" alt="List of Linux Distros in powershell" width="50%" height="50%">

To install your required distro in our case Ubuntu-24.04

```
wsl --install -d Ubuntu-24.04
```

You can replace <Ubuntu24.04> with whatever distribution of Linux you want to use.
When asked for a Unix username and password, use whichever username and password you want.
Note: use lowercase letters in username and the password will not be visible when typing, so carefully type your password.

<img src ="https://github.com/user-attachments/assets/fa448115-bbcd-4d6c-9ee4-e18812609541" alt="Successful Ubuntu install">


You can also use the following YouTube video for a more visual step-by-step guide.

[Ubuntu On WSL](https://youtu.be/7Sym3uL6YWo?si=1HF1zHWLwNf9XjQW)

Next, check the state of your wsl type 

```
wsl -l -v
```

<img src="https://github.com/user-attachments/assets/ebb14197-cfff-4f4b-99cb-11d88a04f7c0" alt="Installed Distros and WSL Version Running" width="50%" height="50%">

## Launch Ubuntu
To launch Ubuntu, either search ___Ubuntu 24.04 LTS___ in the Start Menu.

<img src="https://github.com/user-attachments/assets/816b4ed6-2215-4d36-9937-43cba551a4c7" alt ="Search Ubuntu 24.04 LTS" width="50%" height="50%">

Or enter the following command in Powershell.

```
wsl -d Ubuntu-24.04
```

<img src="https://github.com/user-attachments/assets/215ad799-0b16-4605-a258-4ea825f3cea2" alt = "Launching Ubuntu via powershell" width="50%" height="50%">


## Update Ubuntu

In the terminal enter the following commands one by one. Enter the password for authentication.

```
sudo apt update
```

<img src="https://github.com/user-attachments/assets/a8b29455-cfef-4d34-ab69-0388be00bbd6" alt= "sudo apt update" width="50%" height="50%">

```
sudo apt upgrade
```

<img src="https://github.com/user-attachments/assets/c35591cd-2af1-4d99-8a23-2621eaa26634" alt="sudo apt upgrade" width="50%" height="50%">


**Note**: _if the update fails, try configuring the DNS within your Ubuntu as mentioned below._

### Configuring DNS
In the terminal, enter

```
sudo nano /etc/resolv.conf
```

and replace the nameserver with either 1.1.1.1 or 8.8.8.8 in the nano editor. Then press Ctrl+S to save and then Ctrl+X to close the nano editor.

Next, enter

```
sudo nano /etc/wsl.conf
```

and paste the following in the nano editor.

```
[network]
generateResolvConf = false
```

Try updating again, it should come through.

## Enable systemd
To enable systems, first open wsl.conf via the following terminal command

```
sudo nano /etc/wsl.conf
```

and paste following

```
[boot]
systemd=true
```

<img src ="https://github.com/user-attachments/assets/fd246961-246a-4ca1-8c6d-95689c82b706" alt="wsl.conf" width="40%" height="50%">


This allows multiple features and packages in your Ubuntu system to be used in the future.
Update Ubuntu once more.
**Note**: _If the update fails again, go through the Configuring DNS steps again and you should be good._

## Install Postfix
Postfix is a popular open-source mail transfer agent (MTA) used to route and deliver emails.
To install Postfix, enter the following command:

```
sudo apt install postfix
```

Enter 'Y' or 'Yes' to continue to install

You will be prompted to _Postfix Configuration_. Select ___Local Only___.

<img src="https://github.com/user-attachments/assets/dadd4632-f856-4956-b334-816f6ae24354" alt="Postfix Configuration"  width ="60%" height="60%">


Enter the system mail name, you can keep it default  or change it.

<img src="https://github.com/user-attachments/assets/0c684ab3-23c3-4187-8a49-1919c93255be" alt="Postfix Config System Mail Name" width="60%" height="60%">


**Note**: _If you get the following error._

<img src="https://github.com/user-attachments/assets/4bef0926-4e4e-4223-b0a9-947f43939a43" alt="Error Installing Postfix" width ="50%" height="50%">


___Perform Following Steps___
Set hostname via the following command

```
sudo hostnamectl set-hostname DESKTOP-94VIJG8
```

<img src="https://github.com/user-attachments/assets/e491fd0d-b487-4c21-869d-0fec2e94b349" alt="set host name" >


Check the hosts via the following command

```
sudo nano /etc/hosts
```

<img src="https://github.com/user-attachments/assets/92f53a43-2724-4645-ae8c-bb4efe96754d" alt="check hosts">


In the nano editor, if the highlighted (.) exists, remove it and that should allow you to complete the installation.

<img src="https://github.com/user-attachments/assets/533e9ada-924a-4dc8-8e70-0204a7567816" alt="Host in Nano editor">


After removing (.)

<img  src="https://github.com/user-attachments/assets/182c6d7d-afda-4360-8055-3721f544e2a6" alt="Corrected Hosts">

Ctrl+S to save and then Ctrl+X to close editor.

## Configure Postfix
Open the main configuration file for postfix

```
sudo nano /etc/postfix/main.cf
```

In the nano editor, Comment out the existing ___myhostname___ and ___mydestination___ with '#' at the start of the line and enter the following lines at the end of the file.

```
# Set the hostname of your mail server
myhostname = localdomain
# Set the domain name
mydomain = localdomain
# Set the origin
myorigin = /etc/mailname
# Local delivery only
inet_interfaces = loopback-only
# Restrict delivery to only local destinations
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
# Mailbox location
home_mailbox = Maildir/
protocols = imap pop3
```

<img src="https://github.com/user-attachments/assets/f512c0ee-8696-4d0f-a881-ddde991f7d0c" alt="postfix main.cf configuration">


## Install Dovecot

Dovecot is used to manage email retrieval for users, allowing them to access their emails stored on the server. 

```
sudo apt install dovecot-core dovecot-imapd dovecot-pop3d
```

<img src="https://github.com/user-attachments/assets/4f2a486f-e8db-4dc6-a4ef-5de5a55a4706" alt="Installing Dovecot">

## Configure Dovecot

Open _Dovecot configuration file_ with the following command

```
sudo nano /etc/dovecot/dovecot.conf
```

In the nano editor, Enter the following line at the end of the file.

```
mail_location = maildir:~/Maildir
```

<img src="https://github.com/user-attachments/assets/fb1e8ed2-4c1e-4ee9-8066-36ee862c3207" alt="Edit in dovecot.conf">

Next, open the _auth config file_ with the following command

```
sudo nano /etc/dovecot/conf.d/10-auth.conf
```

Uncomment the highlighted line of _plain_text_authntication= yes_ and set it to no

<img src="https://github.com/user-attachments/assets/2a10fd10-1e97-45ba-b2ac-7a7a371e2249" alt="Edit in Auth File">





