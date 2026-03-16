
KVER=$(make kernelrelease)
echo "$KVER"

mkdir -p "$HOME/kernel-artifacts"  
make -j"$(nproc)"  
sudo make modules_install  
sudo dracut --force "$HOME/kernel-artifacts/initramfs-$KVER.img" "$KVER"  
sudo chown "$USER:$USER" "$HOME/kernel-artifacts/initramfs-$KVER.img"  
