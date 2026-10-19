# Ancora-Education-Ucertify-Lab59
# Managing Encrypted Filesystems

> **Original Lab Source**
> 
> This lab was available through:
>
> [https://ancoraeducation.ucertify.com/app/?func=navigate_items&item_sequence=12]

## Objective of the Lab
In this lab, you will learn to manage encrypted filesystems. The Encrypted File System, or EFS, provides an additional level of security for files and directories. It provides cryptographic protection of individual files on NTFS file system volumes using a public-key system. 
## Instructions
### STEP 1
From the desktop, open the Terminal window. 
### STEP 2 
Execute the following command to load the necessary kernel module:
```bash
modprobe dm-crypt
```
### STEP 3 
Execute the following command to encrypt the partition: 
### Caution
* When asked for confirmation, enter YES
 ```bash
 cryptsetup --verbose --verify-passphrase luksFormat /dev/sdb1
  ```
### STEP 4
When asked for a passphrase and asked to verify the passphrase, enter uC@135246
### Caution 
* The passphrase will not be visible.
* Enter the passphrase as uC@135246, whenever asked.
### STEP 5 
Execute the following command to unlock the partition:
```bash
cryptsetup luksOpen /dev/sdb1 repo
```
### STEP 6
Execute the following command to create the filesystem:
```bash
mkfs -t ext4 /dev/mapper/repo
```
### STEP 7 
Execute the following commands to manually mount the filesystem and verify it (Note: Enter one command at a time.):
```bash
mount /dev/mapper/repo /repo
```
```bash
mount
```
### STEP 8
Enter the following command to open the /etc/crypttab file:
```bash
nano /etc/crypttab
```
### STEP 9 
Add the following line to configure the filesystem to mount automatically and press CTRL+X, press y and then press the Enter key:
```bash
repo /dev/sdb1 none
```
### STEP 10 
Enter the following command to open the /etc/fstab file:
```bash
nano /etc/fstab
```
### STEP 11 
Add the following line to the /etc/fstab file and press CTRL+X, press y and then press the Enter key:
```bash
/dev/mapper/repo /repo ext4 defaults 0 1
```
## Disclaimer

This repository is for **educational and personal learning purposes only**.  

The original lab content belongs to **uCertify / Ancora Education** and remains their copyrighted material.  
This repository is not affiliated with, endorsed by, or sponsored by uCertify or Ancora Education.  

No copyright infringement is intended.  
Use of any tools or techniques mentioned here should only be performed in authorized, legal environments.
