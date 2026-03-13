# Day 1: Linux User Setup with Non-Interactive Shell

# Task

To accommodate the backup agent tool's specifications, the system admin team at `xFusionCorp Industries` requires the creation of a user with a non-interactive shell. Here's your task:

Create a user named `javed` with a non-interactive shell on `App Server 1`.

# Solution

We need to create the user on `App Server 1`. We are currently logged in as `thor` on Jump Host Server (`jump-host`).The documentation tell us that the host of the server is `stapp01` and the is a user named `tony` with the password `Ir0nM@n` who have access to this server.

1) Log in to `stapp01`:
    ```bash
    ssh tony@stapp01
    ```

2) Create a new user named `javed`:
    ```bash
    sudo adduser javed
    ```
    I am using `adduser` instead of `useradd` because I prefer using a more minimalistic approach has the task doesn't mention `home`, `password`, etc.

3) Disable the interactive shell:
    ```bash
    sudo usermod -s /sbin/nologin javed
    ```

## SRE lens
- Disabling interactive shell is a common practice for service accounts as it reduces the attack surface.
- In production we prefer using IAM, or similar instead of manual `usermod`
