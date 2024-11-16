# Steps to Increase RAM and Storage on VirtualBox Ubuntu

## Increasing RAM

1. **Shut down the VM:**

   - Ensure the Virtual Machine (VM) is powered off.

2. **Adjust VM Settings:**

   - Open VirtualBox and select your Ubuntu VM.
   - Go to `Settings` -> `System` -> `Motherboard` tab.
   - Adjust the `Base Memory` slider to allocate more RAM.

3. **Start VM:**
   - Start the VM and verify the new RAM allocation.

## Increasing Storage

1. **Open VirtualBox:**

   - Launch VirtualBox.

2. **Access Virtual Media Manager:**

   - Go to `File` -> `Virtual Media Manager` (or use `Ctrl + D` shortcut).

3. **Check Disk Space:**

   - Open your Ubuntu VM and check disk space using `df -h`.
   - If the disk space hasn't updated, proceed with the next steps.

4. **Install GParted:**

   - Open a terminal in Ubuntu.
   - Install GParted if not already installed:
     ```bash
     sudo apt-get update
     sudo apt-get install gparted
     ```

5. **Resize Partition with GParted:**

   - Launch GParted:
     ```bash
     sudo gparted
     ```
   - Select `/dev/sda` (your main disk).
   - Right-click on `/dev/sda3` (your root partition) and choose `Resize/Move`.
   - Adjust the partition size by dragging the handle or entering the new size.

6. **Unmount if Necessary:**

   - If the partition is read-only, right-click on `/dev/sda3`, select `Unmount`, then resize as in step 5.

7. **Apply Changes:**

   - Click `Resize/Move` to apply the changes.
   - Once you've resized the partition, click on the green checkmark icon or Apply button in GParted to execute the resize operation.

8. **Restart Ubuntu:**
   - After resizing, restart your Ubuntu VM to apply the changes.
