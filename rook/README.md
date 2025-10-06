# Preparing new osd disks

1.  cryptsetup luksFormat -c aes-xts-plain64 -s 512 -h sha512  /dev/sdb /root/ssd.key
    root@kirk:/home/felix# blkid /dev/sdb
    /dev/sdb: UUID="673d82fa-747c-45e0-be89-0c4524682d8d" TYPE="crypto_LUKS"

Update /etc/crypttab

crypt_ssd       UUID="6c48bffb-5231-4426-b428-abd50f60b1e8"     /root/ssd.key   luks


cryptdisks_start crypt_ssd

Place LVM on top of LUKS