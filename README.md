# comfyui-amd-container (WIP)

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
- dkms
- amdgpu-dkms (required to properly run AMD GPU in containers)

### Preparation

Kernel modules for AMD GPU is required. For that, you need:
- Linux headers (including generic) with build tools like gcc, g++, etc.
- amdgpu-install available on AMD website ([doc](https://rocm.docs.amd.com/projects/install-on-linux/en/latest/install/amdgpu-install.html))

### Installation

When you have amdgpu-install, install it `sudo apt install ./amdgpu-install-<version>`. Now you can run it with arguments to only setup dkms kernel modules: `sudo amdgpu-install --usecase=dkms`. To verify it's installed properly: `dkms status`.

I don't got further as all of this is in the docs already and we only particularly need this one.

## TODO

- [ ] clean documentation
- [ ] ensure compose file compatibility with Docker
- [ ] add DependaBot to keep ComfyUI up to date
- [x] set a defined ComfyUI version
- [x] use GitHub Actions to build and push the container to GitHub registry (and remove the build step in compose)
