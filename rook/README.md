# Preparing new osd disks
1. Create PV
2. Create LV
3. Create LUKS on LV (Rook does not support setting the encrypted OSD flag on LVM)
4. Add the crypt device to rook configuration

# Versuch 2
1.  cryptsetup luksFormat -c aes-xts-plain64 -s 512 -h sha512  /dev/sdb /root/ssd.key
    root@kirk:/home/felix# blkid /dev/sdb
    /dev/sdb: UUID="673d82fa-747c-45e0-be89-0c4524682d8d" TYPE="crypto_LUKS"

Update /etc/crypttab

crypt_ssd       UUID="673d82fa-747c-45e0-be89-0c4524682d8d"     /root/ssd.key   luks


cryptdisks_start crypt_ssd

Place LVM on top of LUKS