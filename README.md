# 🧰 ZFS Kernel Module Installation Guide for `6.6.63-ky`

This guide walks you through installing precompiled ZFS kernel modules for **Linux kernel version 6.6.63-ky** (Orangepirv2_1.0.0_ubuntu_noble_server_linux6.6.63 from orangepi website).

> **⚠️ Prerequisites:**
> - Your system must be running **kernel 6.6.63-ky**
> - You need **root/sudo** privileges

---

## 📦 Step 1: Transfer the Archive

Copy the archive to your target system.

Example using `scp`:

```bash
scp zfs-6.6.63-ky.tar.gz user@target-ip:/home/user/
```

---

## 📂 Step 2: Extract the Archive

On the target system:

```bash
cd ~
tar -xzf zfs-6.6.63-ky.tar.gz
```

---

## 🧬 Step 3: Copy Modules to Kernel Directory

Create the kernel module path and copy the files:

```bash
sudo mkdir -p /lib/modules/6.6.63-ky/updates/dkms
sudo cp -r ~/zfs-modules/updates/dkms/* /lib/modules/6.6.63-ky/updates/dkms/
```

Copy the `modules.*` metadata:

```bash
sudo cp ~/zfs-modules/modules.* /lib/modules/6.6.63-ky/
```

---

## 🔄 Step 4: Regenerate Module Dependencies

```bash
sudo depmod -a 6.6.63-ky
```

---

## 📥 Step 5: Load the ZFS Kernel Module

```bash
sudo modprobe zfs
```

---

## ⚙️ Step 6: Install Userland Tools

```bash
sudo apt update
sudo apt install zfsutils-linux
```

---

## ✅ Step 7: Verify the Installation

Confirm the module is loaded and working:

```bash
sudo zfs version
lsmod | grep zfs
```

---

🎉 You're done! ZFS is now installed and ready on your system.
