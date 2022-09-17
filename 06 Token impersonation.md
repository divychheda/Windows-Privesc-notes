# Token Impersonation
- Just like in active directory
https://github.com/divydividivu/PEH-AD-notes/blob/main/03_Post-compromise-exploitation.md
- But a win pc can have a administrator token too (hence in privesc).
- From payloadallthethings:
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Windows%20-%20Privilege%20Escalation.md#eop---impersonation-privileges
Note: int he link above `SeAssignPrimaryToken` is same as Impersonate Token : `SeImporsonatePrivilege'.

## Potato Attacks
https://foxglovesecurity.com/2016/09/26/rotten-potato-privilege-escalation-from-service-accounts-to-system/ <br>

- Follow steps here:
https://medium.com/r3d-buck3t/impersonating-privileges-with-juicy-potato-e5896b20d505
