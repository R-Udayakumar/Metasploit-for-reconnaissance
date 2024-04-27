# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
## OUTPUT:
![Screenshot 2024-04-24 220627](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/ae105eb3-04b0-41be-b58b-bab2b16db044)


Invoke msfconsole:

![Screenshot 2024-04-24 221006](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/459b09ca-5d83-4a4f-9154-d3216eee02c4)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![Screenshot 2024-04-24 221125](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/03dcb2a8-d525-425e-9430-3eeb80750e06)


## Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:
![image](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/74da8942-68dd-4899-959e-3b59b9142f23)

step4:  use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24

## OUTPUT:
![image](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/004f0c12-2042-465a-a578-ec7dd11e8f19)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:
![image](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/dd5d77a2-7f31-4eef-9c36-c3eb05dbcc7a)

Search is a powerful command in Metasploit that you can use to find what you want to locate.
msf >search name:google type:exploit
The info command provides information regarding a module or platform,

## OUTPUT
![image](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/eee529e5-d62f-4f7b-9f80-3ebb312dd246)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
![image](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/cef63992-e840-43d3-a909-f392396c40a9)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql
![Screenshot 2024-04-27 140639](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/3b38197f-b524-49c5-91ed-dc71c21d04d3)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version
![image](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/1122e9fb-7a6a-4c41-b38a-864031d303b8)

Use the set rhosts command to set the parameter and run the module, as follows:
![image](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/aea69ad6-2c6c-4bf1-b1c8-a076093340d6)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
![image](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/fac75fb5-c25e-4179-a179-fb2aba861de8)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true
![image](https://github.com/R-Udayakumar/Metasploit-for-reconnaissance/assets/118708024/90454a17-1c27-4406-a0c0-751d5db6d97f)





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
