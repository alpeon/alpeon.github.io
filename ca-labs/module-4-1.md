---
layout: default
title: Lab 1 - Adjust the Monitoring Settings 
parent: Module 4
---

## Module 4 - Lab 1 : Adjust the Monitoring Settings  
    
## Objective(-s):
- Edit the monitord.conf.
- Restart the opennebula daemon.


> [!WARNING]
> The tasks in this section must be executed either with the elevated privileges. This guide assumes that you've switched to the "root" user!
    
    
#	Edit the monitord.conf.
    
    
## 4.1.1

Using your preferred text editor, as root, edit the **/etc/one/monitord.conf** file.

```console[]
vi /etc/one/monitord.conf
```


## 4.1.2

Locate the **PROBES_PERIOD** section and set the **SYSTEM_HOST** value from **600** to *180**.

```console[1,3]
PROBES_PERIOD = [
    BEACON_HOST    = 30,
    SYSTEM_HOST    = 180,
    MONITOR_HOST   = 120,
    STATE_VM       = 5,
    EXEC_VM        = 5,
    MONITOR_VM     = 30,
    SYNC_STATE_VM  = 180
]
```

Then save the file. 


### Restart the opennebula daemon.

    
## 4.1.3

Restart the opennebula daemon.

```console[]
systemctl restart opennebula
```
    
# Congratulations, you've completed the assignment!