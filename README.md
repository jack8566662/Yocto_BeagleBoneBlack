# Yocto_BeagleBoneBlack

Yocto build system for creating custom Linux distributions for the BeagleBone Black.

## Target Hardware

**BeagleBone Black** - An open-source hardware single-board computer
- Processor: AM3358 1GHz ARM Cortex-A8
- Memory: 512 MB DDR3 RAM
- Storage: 4GB eMMC on-board storage
- Connectivity: Ethernet, USB, HDMI
- GPIO: 65 digital I/O pins

## Development Environment

- **Host OS**: Windows 11
- **Build Platform**: Docker (recommended image: `embeddedlinuxacademy/yocto-buildcontainer` based on `ubuntu:20.04`)

Notes:
- The recommended build container creates a non-root build user and includes common Yocto/bitbake dependencies.
- Use the `Remote - Containers` (Remote Development) and `Docker` extensions in VS Code to attach to the running container for editing and builds.

## SETUP
See [SETUP.md](SETUP.md) for full instructions on creating the Docker build container, configuring WSL2 on Windows, and installing required packages.

## References

- [Yocto Project Quick Start](https://docs.yoctoproject.org/4.0.7/brief-yoctoprojectqs/index.html)
- [Yocto Build Host Packages](https://docs.yoctoproject.org/4.0.7/brief-yoctoprojectqs/index.html#build-host-packages)