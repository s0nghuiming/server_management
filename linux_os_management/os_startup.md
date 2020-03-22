### 1. CentOS update grub (using UEFI)
vim /etc/default/grub
grub2-mkconfig -o "$(readlink /etc/grub2-efi.cfg)"
