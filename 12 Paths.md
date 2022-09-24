## binPath
### Recon
- Run accesschk to see all service names where we have write access:
```
accesschk64.exe -uwcv Everyone *
```
- See service where we have SERVICE_CHANGE_CONFIG perm.
- Can also use `PowerUp.ps1`, check under 'Checking service permissions`.
- Query the service:
```
sc qc <service name>
```

### Exploitation
- Since we can change the config. we can set the binPath to a malicious command. Like add user.
```
sc config <service name> binpath= "net localgroup administrators user /add"
```
- Restart the service might get an error but user will be added.

## Unquoted Service Path
- Look in PowerUp output for unquoted service path, notice all where the “BINARY_PATH_NAME” field displays a path that is not confined between quotes.
- If path is `C:\Program Files\Common Files\svc.exe`, windows check first for an exe `C:\Program.exe` then `C:\Program Files\Common.exe` and so on till something existing is found.
- So we can insert malicious file there.
- Restart service to get a shell.
