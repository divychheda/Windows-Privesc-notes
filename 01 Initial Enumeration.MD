# 01 Initial Enumeration
- Once we get low-level privilege on a machine, we again go to our roots - scanning and enum for privesc

## a) System Enumeration

## A very basic enum command - systeminfo 
- to get basic OS info and system arch / type

## wmic qfe
- wminc (windows management instrumentation cli)
- qfe (quick fix enginnering)
- it basically returns info about latest patches/updates - their type, hottfixID, time of installation etc. 

## wmic logicaldisk 
- to get names and info of all the drives in the system 
- use get <heading> to get only that column, e.g wmic logicaldisk get caption

## b) User Enumeration

## whoami 
- current user

## whoami /priv
- the privileges of the current user

## whoami /groups
- groups, current user is involved in

## net user
- the diff users on the machines (excluding the services like iisapppool)
- info about a particular user by :- net user <username>

## net localgroup <group-name>
- to get list of members of that group

## c) Network Enumeration

## ipconfig
- info about the network i.e. Gateway, IP, DNS/Domain Controller etc
- ipconfig /all - for more info

## arp -a
- see our arp table (maping of ip to mac addr)
- see if any address seems suspicious 

## route print 
- to get routing information

## netstat -ano 
- info about services an their ports in the internal network
- very important

## d) Password Enum

## findstr /si password *.txt *.ini *.config
- to find every instane of 'password' in these files 
- run this in the directory you want to find these files

## look at the website resources/cheatsheets given at the start of the couse
- payloadallthings is pretty nice

## e) Antivirus and Firewall Enum

## sc query windefend
- info about windows firewall and its state

## sc queryex type=service
- info about all the services 
- used to know about third party antivirus

## netsh advfirewall firewall dump
- modern command for info about firewall (doesnt work always)

## netsh firewall show state
- older command that works always

## netsh firewall show config
- to show the configuration of firewall




