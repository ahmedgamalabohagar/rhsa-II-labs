# Lab 1: LVM-Storage-Management

## Objective

- Understand how to manage Linux storage using LVM (Logical Volume Manager).
- Create and manage Physical Volumes (PV), Volume Groups (VG), and Logical Volumes (LV).
- Format and mount a Logical Volume with the XFS filesystem.
- Configure persistent mounting using /etc/fstab.
- Extend an existing Logical Volume and resize the filesystem.
- Practice verifying storage changes using commands like lsblk, df -h, and lvs.


## Steps

  ### 1. display storage devices and partitions
  ```bash
     lsblk
```
 [![](Images/2-alice-info.jpg)](Images/2-alice-info.jpg)

  ### 2. Create a new group
  ```bash
     sudo groupadd developers
  ```
  ### 3. add user to group developers
  ```bash
     sudo usermod -aG developers alice
  ```



  ### 4 . verify user details 
  ```bash
   id alice
```
[![](Images/2-alice-info.jpg)](Images/2-alice-info.jpg)
    
  - or Display the contents of the /etc/group file and view member of developers group
[![](Images/1-user-addedTo-developerGroup.jpg)](Images/1-user-addedTo-developerGroup.jpg)

 ### 5. change password expire date
  ```bash
     sudo usermod -e 2026-04-24 alice
  ```
 ### 6. verify password details
  ```bash 
      sudo cat /etc/shadow
```
[![](Images/3-verify-expire-date.jpg)](Images/3-verify-expire-date.jpg)
  - Display the content of /etc/shadow file to verify info

 ### 7. Configure sudo for one of them
  ```bash
       sudo usermod -aG wheel alice
  ```
  [![](Images/4-addTo-wheel.jpg)](Images/4-addTo-wheel.jpg) 
    
  ## Challenges
  - At first, I tried setting the password using:
```bash
sudo usermod -p password alice
```
-This stored the password as plain text in /etc/shadow, which is a security risk.
- To fix this, I switched to using the passwd command:
  ```bash
  sudo passwd alice
  ```
  -This stored the password securely as a hash instead of plain text.


