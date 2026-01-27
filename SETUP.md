# Yocto Build Setup Guide

## Prerequisites

Before starting the Yocto build process, you need to set up the build host with required packages.

### Option 1: Official Yocto Documentation

For comprehensive setup instructions, refer to the official Yocto Project Quick Start guide:
- [Yocto Project 4.0.7 Quick Start - Build Host Packages](https://docs.yoctoproject.org/4.0.7/brief-yoctoprojectqs/index.html#build-host-packages)

### Option 2: Quick Installation via CLI

Run the following command in your Ubuntu 22.04 Docker container to install all required packages:

```bash
apt install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3 xterm python3-subunit mesa-common-dev zstd liblz4-tool
```

## Cloning Poky

Poky is the reference implementation of Yocto Project. Clone it with the kirkstone branch:

```bash
git clone git://git.yoctoproject.org/poky -b kirkstone
```

