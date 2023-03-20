# ArchlinuxarmAmlogic
steps to run archlinuxarm on amlogic devices


## PS: This guide is very old, and you could probably get of with installing archlinuxarm from the offical https://archlinuxarm.org website.


1. download the archlinuxarm old russian version .img.xz file  http://mirror.yandex.ru/puppyrus/2a-aarch64/img/  and flash it to an sdcard with balenaetcher or rufus

2. replace the archlinuxarm russian version boot directory with the one from manjaro https://drive.google.com/drive/folders/1ht_SAM_o-wnkeCjCoSZR7DMqQtGYoWjy?usp=sharing  (thank me later lol)
 and configure to acording to your box. after configuring it, edit the extlinux.conf file in the  [boot pariton/boot/extlinux/extlinux.comf] in the last line of the extlinux.conf file there should be a thing like this "root=PARTUUID=fd07d63e-02" remove that bit and replace it with "root=LABEL=ROOTFS" and your now done with the boot pariton for now.

3. remeber the password for the live and root user is "woofwoof" (without the tags)

4. run the command "sudo pacman -Syy" to refresh the mirrorlist and then run the "sudo pacman -S archlinuxarm-keyring" too and then run the command "sudo pacman-key --init" and also run the command "sudo pacman-key --populate archlinxuarm" to initialize the pacman keyring.

5. run the command "sudo pacman -Syu --force" to forcefully update the system because its too old. and then reboot (say Y to any promts), and then run the command sudo pacman -S linux-aarch64-rc to install the rc kernel. 

6. use another computer with linux and copy the “iniramfs-linux.img” from the [archlinuxarmROOTParition/boot/iniramfs-linux.img] and paste it in the [archlinuxarmBOOTParition] (remove the old initramfs-linux.img from the archlinuxarmBOOTPartition), after that copy the “Image" from the [archlinuxarmROOTParition/boot/Image] and paste it in the [archlinuxarmBOOTParition] (remove the old "Image" from the archlinuxarmBOOTPartition),

7. reboot the system into archlinux and welcome to archlinuxarm running on your tiny android tv box.

8. after fullying installtalling archlinux. if u try to download something from pacman for exmaple nano with the command "sudo pacman -S nano" it might give an error saying that file exists in fileystem, to fix that u simply have to type this command instead "sudo pacman -S nano --overwrite '*'  " that should get rid of the error.

 P.S if you want to change the system lanuage from russian to english follow these steps
1. edit the file in /etc/locale.gen and uncomment the first locale and save and exit and then edit the file in /etc/locale.conf and replace the russian locale to the one you uncommented in the /etc/locale.gen file and run the command "locale-gen" in the terminal and reboot and your done
