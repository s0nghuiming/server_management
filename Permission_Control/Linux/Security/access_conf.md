# access.conf

File: /etc/security/access.conf

For Ubuntu (>18.04), sshd comments the access.conf at /etc/pam.d/sshd. Uncomment the following line 
to enable access.conf in ssh login.

```text
# Uncomment and edit /etc/security/access.conf if you need to set complex
# access limits that are hard to express in sshd_config.
account  required     pam_access.so
```

For CentOS, sshd allows access.conf by default.
