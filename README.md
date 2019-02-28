# dgx-selinux

## Introduction
This project contains the SELinux policies used in DGX products.

## Building and debugging
The policy module builds require that the following packages are installed:

    sudo yum install selinux-policy selinux-policy-devel selinux-policy-base libselinux-utils policycoreutils policycoreutils-python

While this is not required, it may be useful for debugging or just evaluating the various policies on the system.

    sudo yum install -y setools-console

setools-console provides the sesearch utility, which is very useful for querying installed modules and such:

    sesearch --help
    sesearch --allow | grep nvidia

## Information
The src/\<policy-module-name\> directories contain the source, Makefiles, and READMEs for each policy module.  Definitions for the macros used in this project can be found in /usr/share/selinux/devel/include.

## Disclaimer
These SELinux policies have only been verified on DGX-1 and DGX-2 on RHEL 7.5 and 7.6.  They are meant to be used as a reference for RHEL-based non-DGX platforms, not verbatim.
