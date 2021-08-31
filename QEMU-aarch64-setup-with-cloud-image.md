## QEMU ARM64 using Ubuntu Cloud Image

```
sudo apt-get install cloud-image-utils qemu-system-arm qemu-efi

# Download ubuntu-18.04-server-cloudimg-arm64.img
qemu-img resize ubuntu-18.04-server-cloudimg-arm64.img +64G

# Create user-data image

cat >user-data <<EOF
#cloud-config
password: asdfqwer
chpasswd: { expire: False }
ssh_pwauth: True
EOF

cloud-localds user-data.img user-data

dd if=/dev/zero of=flash0.img bs=1M count=64
dd if=/usr/share/qemu-efi/QEMU_EFI.fd of=flash0.img conv=notrunc
dd if=/dev/zero of=flash1.img bs=1M count=64

# Launch QEMU 
qemu-system-aarch64 -M virt -cpu cortex-a57 -device rtl8139,netdev=net0 -m 4096 -netdev user,id=net0 -nographic -smp 4 -drive \
"if=none,file=ubuntu-18.04-server-cloudimg-arm64.img id=hd0" -device virtio-blk-device,drive=hd0 -drive "file=user-data.img,format=raw" \
-pflash flash0.img -pflash flash1.img

```
