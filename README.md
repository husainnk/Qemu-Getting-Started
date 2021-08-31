# Qemu-Getting-Started
QEMU Learnings

### QEMU Terms

#### qcow2
qcow2 is a file format for disk image files used by QEMU. It stands for "QEMU Copy On Write" and uses a disk storage optimization strategy that delays allocation of storage until it is actually needed.
Some Benefits of qcow2 

    - Smaller file size, even on filesystems which don't support holes (i.e. sparse files)
    - Copy-on-write support, where the image only represents changes made to an underlying disk image
    - Snapshot support, where the image can contain multiple snapshots of the images history
    - Optional zlib based compression
    - Optional AES encryption

#### Cloud Image
Not specific to QEMU, but you might come up with this term while trying QEMU.
For installing linux distribution like ubuntu, we usually use the installer image and follow the steps in the installer and configure the OS for our requirement.
Its takes more than a hour and it is fine for single desktop. But in servers, there will be a lot of devices and you cannot follow the desktop installation for each device.
So the cloud image, comes with pre-installed configurations that is easier to setup in servers and also in QEMU.


