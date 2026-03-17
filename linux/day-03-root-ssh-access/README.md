# Day 3: Secure Root SSH Access

# Task

Following security audits, the `xFusionCorp Industries` security team has rolled out new protocols, including the restriction of direct root SSH login.

Your task is to disable direct SSH root login on all app servers within the `Stratos Datacenter`.

# Solution

1) First, we need to SSH into the first App Server.
```bash
ssh tony@stapp01
```

2) Then, we need to find how to disable root access for the whole system. The sshd system-wide configuration file is located here : `/etc/ssh/sshd_config`.
```bash
vim /etc/ssh/sshd_config

# lines before ...
PermitRootLogin yes # change it to 'no'
```

As we can see, this configuration allows root login. To disable this option we can set it to 'no'. See `man 5 sshd_config` for more information.

3) Then we must restart SSH.
```bash
sudo systemctl restart sshd
```

4) Repeat for `stapp02` and `stapp03` :)

## SRE lens
- Disabling root SSH login is a standard practice as root has unrestricted privileges.
- Prefer key-based authentication over passwords for all accounts.
- In production, changes to `sshd_config` must go through a change management process to avoid server inaccessibility. 