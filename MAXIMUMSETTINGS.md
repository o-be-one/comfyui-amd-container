# MaximumSettings User Guide (AMD GPU Setup)

**Prerequisites**: This guide complements the main [README.md](README.md) and requires a **MaximumSettings** "Bare Metal" instance (tier 4).

## Host Requirements

MaximumSettings instances use generic AMD Mesa drivers. For advanced AI workloads:

1. **Update the build tools**:
```bash
sudo apt install gcc-14 g++-14
```

2. **Install specific kernel headers**:  
[Download headers for kernel 6.10.10](https://mirrors.portworx.com/mirrors/https/kernel.ubuntu.com/mainline/v6.10.10/amd64/linux-headers-6.10.10-061010-generic_6.10.10-061010.202409121037_amd64.deb)  
```bash
sudo apt install ./linux-headers-6.10.10-generic_6.10.10-061010.202409121037_amd64.deb
```

3. **Verify the installation**:  
```bash
dpkg -l | grep linux-headers-6.10.10-061010-generic
```

4. **Reboot the system**:  
```bash
sudo reboot
```

**Note**: If your kernel is different from 6.10.10, adjust the version numbers in the commands.

## Next Steps

Proceed with the main [README.md](README.md) to:  
1. Install ```amdgpu-dkms```
2. Start the ComfyUI container