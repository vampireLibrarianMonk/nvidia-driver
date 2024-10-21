# NVIDIA Driver Installation with Common Options and Flags

### 1. Identify Your NVIDIA GPU:
First, identify your GPU model using the following command:
```bash
lspci | grep -i nvidia
```

### 2. Check Available NVIDIA Drivers:
To find out which NVIDIA drivers are available for your GPU, use the following command:
```bash
ubuntu-drivers devices
```
This will list the recommended driver, as well as other available driver options.

### 3. Install the Recommended NVIDIA Driver:
To install the recommended driver, run:
```bash
sudo apt install nvidia-driver-<version>
```
Replace `<version>` with the recommended driver version (e.g., `nvidia-driver-535`).

### 4. Advanced Options with NVIDIA Driver Installation:
You can customize the installation with the following additional flags:

- **Prevent automatic installation of recommended driver:**
   ```bash
   sudo ubuntu-drivers list
   ```

- **Install the Latest Proprietary Driver:**
   ```bash
   sudo apt install nvidia-driver-<version>
   ```

- **Force Installation:**
   ```bash
   sudo apt install --reinstall nvidia-driver-<version>
   ```

- **Minimal Installation (Skip dependencies):**
   ```bash
   sudo apt install --no-install-recommends nvidia-driver-<version>
   ```

- **Specify Exact Driver Version:**
   ```bash
   sudo apt install nvidia-driver-<version>=<specific-version>
   ```

   Example:
   ```bash
   sudo apt install nvidia-driver-470=470.57.02-0ubuntu1
   ```

### 5. Reboot the System:
After the installation is complete, reboot your system to apply the changes:
```bash
sudo reboot
```

### 6. Verify NVIDIA Driver Installation:
After rebooting, verify that the NVIDIA driver is installed and functioning by running:
```bash
nvidia-smi
```

### 7. Remove Old NVIDIA Drivers:
If you need to remove old or unused NVIDIA drivers, use:
```bash
sudo apt-get purge nvidia*
```

### 8. Install NVIDIA Settings Application (Optional):
To manage the NVIDIA GPU settings, you can install the NVIDIA settings tool:
```bash
sudo apt install nvidia-settings
```

### 9. Handle Driver Conflicts (Optional):
If you face any issues due to previous installations, you can blacklist nouveau (the open-source NVIDIA driver):
```bash
echo "blacklist nouveau" | sudo tee /etc/modprobe.d/blacklist-nouveau.conf
sudo update-initramfs -u
sudo reboot
```
