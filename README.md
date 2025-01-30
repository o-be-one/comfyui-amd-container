# comfyui-amd-docker (WIP)

**Work in Progress**

Run ComfyUI in container (including Podman) using your AMD GPU graphic card.
*Built to work with Podman for now.*

As I run Apple systems at home and play games, I have a cloud instance from a provider near me. Here the spec I have with them as bare metal ([MaximumSettings setup](#maximumsettings-setup)):

- CPU: AMD 7800X3D
- GPU: AMD 7900XTX
- RAM: 32go DDR5
- Linux Mint 22

## Installation

### Requirements

#### Hardware

- an AMD GPU with enough VRAM that supports rocm (not integrated)
- enough ram

#### Software

- podman
- podman-compose
- amdgpu-dkms (required to properly run AMD GPU in containers)
- dkms

### Preparation

Kernel modules for AMD GPU is required. For that, you need:
- Linux headers (including generic) with build tools like gcc, g++, etc.
- amdgpu-install available on AMD website ([doc](https://rocm.docs.amd.com/projects/install-on-linux/en/latest/install/amdgpu-install.html))

### Installation

When you have amdgpu-install, install it `sudo apt install ./amdgpu-install-<version>`. Now you can run it with arguments to only setup dkms kernel modules: `sudo amdgpu-install --usecase=dkms`. To verify it's installed properly: `dkms status`.

I don't got further as all of this is in the docs already and we only particularly need this one.

## MaximumSettings setup

MaximumSettings provides setup with AMD mesa drivers that are not advanced enough for some AI use. Fortunately, as I made the choice to use containers so requirements on host were quite minimal as only amdgpu-dkms was required.

### Prepare host

Bare metal comes with all build tools. I only needed to upgrade to gcc-14, g++-14 and to install linux-headers-6.10.10-generic. While gcc and g++ are available in the repo, linux-headers-generic for this kernel version are not.
Check the kernel version with `uname -r`, following will be about kernel 6.10.10 so consider to adjust what you read accordingly.

[Download Linux headers generic for 6.10.10 here](https://mirrors.portworx.com/mirrors/https/kernel.ubuntu.com/mainline/v6.10.10/amd64/linux-headers-6.10.10-061010-generic_6.10.10-061010.202409121037_amd64.deb), and then run `sudo apt install ./linux-headers-6.10.10-generic_6.10.10-061010.202409121037_amd64.deb`. You can reboot, but I'm not sure I needed to.

You are all set, you can follow the [Readme from the requirements](#requirements) to install amdgpu-dkms and start your container.

## TODO

- [ ] ensure compatibility with Docker
- [ ] use GitHub Actions to build and push the container to GitHub registry (and remove the build step in compose)