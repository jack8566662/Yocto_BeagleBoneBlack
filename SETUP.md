# Build Environment Setup

## Docker
For full instructions on creating the Docker build container, configuring WSL2 on Windows, and installing required packages.

Quick checklist:
- Use the Embedded Linux Academy build container: https://github.com/embeddedlinuxacademy/yocto-buildcontainer
- Watch the demo for a quick container run: https://www.youtube.com/watch?v=vl8RBLmGxPg
- After attaching to the container, create your project folder in the build user's home (WSL2-backed filesystem):

```bash
cd ~
mkdir -p yocto_project
cd yocto_project
```

If you use the recommended Docker build container (see below) based on `ubuntu:20.04`, run this inside the container to install required packages:

```bash
apt update
apt install -y gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3 xterm python3-subunit mesa-common-dev zstd liblz4-tool
```

## Cloning Poky

Poky is the reference implementation of Yocto Project. Clone it with the kirkstone branch:

```bash
git clone git://git.yoctoproject.org/poky -b kirkstone
```

## Using Visual Studio Code

For development and editing inside the container use the VS Code extensions:
- `Remote - Containers` (Remote Development) and `Docker` extension.

Steps:
- Open VS Code on the host.
- Use the Docker extension to locate and attach to the running container, or use `Remote - Containers: Attach to Running Container...`.

## UInitialize Yocto Build Environment
```
cd poky
source oe-init-build-env
```

Create Source Folder (not necessary, but very much recommended)
From build folder run the following command

```
mkdir ../../sources
```

modified `local.conf` in build folder

Please configure the target `MACHINE` for `beaglebone-yocto` building image
```
MACHINE ?= "beaglebone-yocto"
#MACHINE ??= "qemux86-64"
```

```
# The default is a tmp directory under TOPDIR.
#
SOURCES = "/home/dev/workspace/yocto_test/sources"
DL_DIR ?= "${SOURCES}/downloads"
SSTATE_DIR ?= "${SOURCES}/sstate-cache"
TMPDIR = "${SOURCES}/tmp"
```

```
# CONF_VERSION is increased each time build/conf/ changes incompatibly and is used to
# track the version of this file when it was generated. This can safely be ignored if
# this doesn't mean anything to you.
CONF_VERSION = "2"
RM_OLD_IMAGE = "1"
INHERIT = "rm_work"
```

## Build Image
```
bitbake core-image-full-cmdline
```