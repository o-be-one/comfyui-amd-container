# MaximumSettings user guide

If you are a customer of MaximumSettings, be happy because this is the provider I used for this project.
Please follow below instructions as some steps are required prior following the [README.md](README.md).

## MaximumSettings setup

MaximumSettings provides setup with AMD mesa drivers that are not advanced enough for some AI use. Fortunately, as I made the choice to use containers so requirements on host were quite minimal as only amdgpu-dkms was required.

### Prepare host

Bare metal comes with all build tools. I only needed to upgrade to gcc-14, g++-14 and to install linux-headers-6.10.10-generic. While gcc and g++ are available in the repo, linux-headers-generic for this kernel version are not.
Check the kernel version with `uname -r`, following will be about kernel 6.10.10 so consider to adjust what you read accordingly.

[Download Linux headers generic for 6.10.10 here](https://mirrors.portworx.com/mirrors/https/kernel.ubuntu.com/mainline/v6.10.10/amd64/linux-headers-6.10.10-061010-generic_6.10.10-061010.202409121037_amd64.deb), and then run `sudo apt install ./linux-headers-6.10.10-generic_6.10.10-061010.202409121037_amd64.deb`. You can reboot, but I'm not sure I needed to.

You are all set, you can follow the [Readme from the requirements](#requirements) to install amdgpu-dkms and start your container.