# nvidia-dgxcache-selinux

## Building
Assuming all required packages have been installed:

    make -f /usr/share/selinux/devel/Makefile

If successful, this should generate a .pp file that can be installed on the system.

    sudo semodule -i nvidia-dgxcache.pp

## Information
DGX systems create a large RAID array that gets mounted to /raid.  The cachefile daemon is then configured to use this mountpoint as its data cache.  To allow for the data cache to be moved this way, we create the nvidia-dgxcache policy module.  This module labels all contents in /raid with cachefilesd_var_t.

## Disclaimer
These SELinux policies have only been verified on DGX-1 and DGX-2 on RHEL 7.5 and 7.6.  They are meant to be used as a reference for RHEL-based non-DGX platforms, not verbatim.
