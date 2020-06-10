# Different SSH keys for multiple accounts in Linux

## Create SSH keys for different accounts

```bash
ssh-keygen -t rsa -C "user1" -f "user1"
```

## Config SSH Identity config file
```text
 #user1 account
 Host bitbucket.org-user1
     HostName bitbucket.org
     User git
     Port 10000
     IdentityFile ~/.ssh/user1
     IdentitiesOnly yes

 #user2 account
 Host bitbucket.org-user2
     HostName bitbucket.org
     User git
     Port 10000
     IdentityFile ~/.ssh/user2
     IdentitiesOnly yes
```

## Git repo

```bash
git clone git@bitbucket.org-user1:user1/your-repo-name.git
```
Or
```bash
git remote set-url origin git@bitbucket.org-user1:user1/your-repo-name.git
```
Or 
```bash
cd your-repo
git config user.name "user1"
git config user.email "user1@example.com"
```
