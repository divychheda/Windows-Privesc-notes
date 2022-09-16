# Privesc using WSL
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Windows%20-%20Privilege%20Escalation.md#eop---windows-subsystem-for-linux-wsl
<br>
- Look for bash.exe and wsl.exe:
```
where /R C:\windows bash.exe
where /R C:\windows wsl.exe
```
- Execute the bash exe found above to step into wsl shell.
- Look at bash history with cmd: `history`.
- Find ways to exploit.
- Here, he found smb creds and smexec to get admin.
