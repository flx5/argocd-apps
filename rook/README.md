# Preparing new osd disks
1. Create PV
2. Create LV
3. Create LUKS on LV (Rook does not support setting the encrypted OSD flag on LVM)
4. Add the crypt device to rook configuration