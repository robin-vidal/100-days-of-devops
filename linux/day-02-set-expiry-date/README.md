# Day 2: Temporary User Setup with Expiry

# Task

As part of the temporary assignment to the `Nautilus` project, a developer named rose requires access for a limited duration. To ensure smooth access management, a temporary user account with an expiry date is needed. Here's what you need to do:

Create a user named `rose` on `App Server 3` in Stratos Datacenter. Set the expiry date to `2027-03-28`, ensuring the user is created in lowercase as per standard protocol.

# Solution

1) We start this lab logged in as `thor` on Jump Host Server (`jump-host`). As the new account needs to be created on `App Server 3` we must SSH into it with the user configured on it.
    ```bash
    ssh banner@stapp03
    ```

2) Next we create the new account while setting the expiry date:
    ```bash
    # 'e' stands for expiry
    sudo adduser -e 2027-03-28 rose
    ```

3) Check if the expiry date is set:
    ```bash
    sudo chage -l rose
    ```

## SRE lens
- In production, prefer centralized IAM (LDAP, etc...) as account lifecycle is automated.