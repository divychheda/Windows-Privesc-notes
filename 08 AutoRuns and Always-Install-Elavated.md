https://tryhackme.com/room/windowsprivescarena#
## Auto-runs
- Files that run automatically.
- Can be running with elevated privileges, if we have excess to modify we can place reverse shell.
- To check for all autoruns - `Autoruns64.exe`, inside click on logon tab and see for something fishy.
- Or you can run `PowerUp.ps1` and it tells about all things exploitable. 
- On find such an executable check for privileges with: 
```
accesschk64.exe -wvu "C:\Program Files\Autorun Program"
```
- If we get - “Everyone” user group has “FILE_ALL_ACCESS” we can exploit it.

## Always install elevated
- a feature thats enabled in some machines allowing to install every program's msi as a admin by default.
- can exploit to execute a rev-shell, add a user to admins group or any such malicious script.
- To check for it:
```
reg query HKLM\Software\Policies\Microsoft\Windows\Installer
```
and
```
reg query HKCU\Software\Policies\Microsoft\Windows\Installer
```
Note: see if the AlwaysInstallElevated” value is 1 (could be in hex).
