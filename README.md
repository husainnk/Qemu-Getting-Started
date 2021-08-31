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

