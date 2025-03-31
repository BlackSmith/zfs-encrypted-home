# zfs-encrypted-home
ZFS for user home directories, with native realtime encryption and compression

This is a simple guide and collection of tools, that make setting up a user home directory on just about any Linux distro - which normally is not an easy undertaking - easy-peasy.

(*This particular document is a work-in-progress.*)

# My notes

```sh
dnf install datamash
curl -o /usr/local/bin/zfs_mount_home.sh https://raw.githubusercontent.com/BlackSmith/zfs-encrypted-home/refs/heads/main/x9sys_zfs_mount-enc-home
chmod +x /usr/local/bin/zfs_mount_home.sh

zfs set canmount=noauto main_pool/user_home
zfs set x9.custom.automount:user=username main_pool/user_home

```

Add this line into `/etc/pam.d/gdm-password`, `/etc/pam.d/login` and `/etc/pam.d/sshd`.

```sh
auth        optional     pam_exec.so expose_authtok debug log=/tmp/file.log /usr/local/bin/zfs_mount_home.sh
```


