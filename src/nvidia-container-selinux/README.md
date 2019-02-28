# nvidia-container-selinux

## Building
Assuming all required packages have been installed:

    make -f /usr/share/selinux/devel/Makefile

If successful, this should generate a .pp file that can be installed on the system.

    sudo semodule -i nvidia-container.pp

## Information
This policy module allows GPU-aware containers to access the files they need.  It assumes that the system is using the default (Red Hat-provided) labeling, and creates a new domain -- nvidia_container_t -- that can be used when starting containers.

nvidia_container_t is then associated with a handful of previously declared attributes and given permissions to container_runtime_tmpfs_t directories.  Lastly, it is allowed to access device nodes that have been labeled with xserver_exec_t and/or xserver_misc_device_t (mainly /dev/nvidia*).

Now with the policy installed, one can use nvidia_container_t to run GPU-aware containers:

    sudo docker run --security-opt label=type:nvidia_container_t --rm nvcr.io/nvidia/cuda nvidia-smi

## Disclaimer
These SELinux policies have only been verified on DGX-1 and DGX-2 on RHEL 7.5 and 7.6.  They are meant to be used as a reference for RHEL-based non-DGX platforms, not verbatim.
