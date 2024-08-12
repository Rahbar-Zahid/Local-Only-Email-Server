# Local-Only-Email-Server
## Setup Environment 
We are running our ubuntu on **WSL**. To setup on wsl follow the following wsl setup guide.
Before we start, make sure you have virtualization enabled in BIOS.
Enable _Virtualization_ and _WSL_ features. For that, in start, Search ___Features on and off___.
![image](https://github.com/user-attachments/assets/a720755c-1508-4ffa-a71f-2a638bc34ef0)

It will open Windows Features. In it find and enable ___Virtual Machine Platform___ and ___Windows subsystem for Linux___.
![image](https://github.com/user-attachments/assets/55b6d2a0-7e10-4c9f-9df7-679bacd15399)

Press Ok and restart PC. 

Afterwards, Open powershell as administrator and run command
`wsl --install`

Make sure you have WSL2 install.
`wsl --status`
