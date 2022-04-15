# Swap

The primary function of swap space is to substitute disk space for RAM memory when physical RAM fills up and more memory is needed.

For example, to create a swap file of `2GB` (128M x 16 = 2048) and to use it, you can use the following command:

```shell
sudo dd if=/dev/zero of=/var/swap.file bs=128M count=16
sudo chmod 600 /var/swap.file
sudo mkswap /var/swap.file
sudo swapon /var/swap.file
```

To add the entry to `/etc/fstab`:

```shell
sudo sed -i '$a # SwapFile\n/var/swap.file  swap  swap  sw  0 0' /etc/fstab
```
