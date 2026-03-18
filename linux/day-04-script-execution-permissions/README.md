# Day 4: Script Execution Permissions

# Task

In a bid to automate backup processes, the `xFusionCorp Industries` sysadmin team has developed a new bash script named `xfusioncorp.sh`. While the script has been distributed to all necessary servers, it lacks executable permissions on `App Server 1` within the Stratos Datacenter.

Your task is to grant executable permissions to the `/tmp/xfusioncorp.sh` script on `App Server 1`. Additionally, ensure that all users have the capability to execute it.

# Solution

1) First we need to login to `stapp01`:
    ```bash
    ssh tony@stapp01
    ```

2) Then we add executable permissions to the script so all users can execute it:
    ```bash
    sudo chmod 755 /tmp/xfusioncorp.sh
    ```
I choose to use `755` over `777` so everyone can read and execute the script but only the owner can modify it.

3) Finally, we try to run the script:
    ```bash
    /tmp/xfusioncorp.sh
    Hello KodeKloud!
    ```

## SRE lens
- Scripts in `/tmp` are a red flag in production because `/tmp` is cleared on reboot. Prefer `/usr/local/bin` or `/opt`.
- Validate script integrity before execution (checksum).