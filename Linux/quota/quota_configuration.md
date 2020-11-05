# Quota Configuration
In this article, I assume you have installed and setup a disk and have installed quota and enabled quota on this disk. If not please go to previous article quota installation [].

## Edit user quota
edquota
## Edit group quota
## Set disk quota
if your mounted disk has the option: 
```text
/dev/sdb1 on /home type xfs (rw,relatime,seclabel,attr2,inode64,logbsize=256k,sunit=512,swidth=512,usrquota)
```
use this command to set quota for user user1.
```bash
setquota -u -F xfs user1 200000 200000 0 0 /dev/sdb1
```
