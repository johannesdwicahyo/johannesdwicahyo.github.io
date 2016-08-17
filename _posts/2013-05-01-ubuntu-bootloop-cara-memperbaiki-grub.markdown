---
title: "Ubuntu Bootloop -- Cara Memperbaiki Grub"
date: 2013-05-01 15:24
categories: ubuntu, bootloop, grub, error, repair
---

Satu lagi masalah yang muncul hari ini adalah Ubuntu saya mengalami bootloop, tanpa henti karena error di Grub setelah saya melakukan perubahan pada partisi yang kurang sesuai. Dan seperti biasa ada cara mudah dan repot, kali ini saya memilih cara repot untuk menyelesaikannya.
<!--more-->
Cara mudahnya adalah menggunakan utility boot-repair. Silahkan dilihat di link-link di bawah untuk langkah-langkahnya. Sementara yang akan saya lakukan adalah perbaikan dari command line. Terasa lebih menantang dan saya rasa bisa lebih berguna untuk pembelajaran.

Setelah membaca-baca dan mencoba-coba, saya akhirnya berhasil memperbaiki Grub Ubuntu saya dengan menggabungkan cara penyelesaian dari beberapa sumber. Anda membutuhkan Live CD Linux untuk melakukan ini, saat melakukan perbaikan saya menggunakan OS Backtrack 5 R3 yang dijalankan melakui usb flashdisk, karena saat ini hanya itu yang saya punya. Disarankan oleh beberapa orang untuk memakai Live CD OS yang persis sama dengan yang akan diperbaiki, jadi misalnya akan memperbaiki Ubuntu 12.04 maka sebaiknya memakai live CD Ubuntu 12.04 juga. Sempat khawatir kalau ini berpengaruh banyak, tapi akhirnya saya berhasil memperbaiki Grub meskipun menggunakan OS yang berbeda.

Anda tentu saja kemudian perlu memboot up komputer anda dengan live cd tersebut. Setelah masuk ke lingkungan live CD anda dapat segera masuk ke terminal, banyak cara untuk melakukan ini, silahkan pilih yang paling nyaman menurut anda. Karena saya menggunakan Backtrack, saya langsung masuk ke interface command line dan mendapat shell root, karena itu saya sebenarnya tidak perlu menambahkan *sudo* untuk setiap command yang akan saya jalankan.

Selanjutnya kita perlu mengetahui di manakah OS Linux yang akan kita perbaiki itu berada. Ada beberapa perintah untuk mengetahui hal ini, bisa dijalankan ke semuanya juga agar lebih yakin. Partisi tempat OS kita berada bisa diketahui dengan melihat tipenya, biasanya **ext4**. Dan paling tidak seharusnya anda juga tahu perkiraan ukurannya, sehingga bisa lebih pasti untuk menemukannya. Dalam kasus saya, partisi tempat OS saya berada adalah di */dev/sda5*.
``` bash
fdisk -l
blkid
df -Th
```
{% img http://i.imgur.com/ct1Pgkr.png %}
{% img http://i.imgur.com/XfqG8Pj.png %}
{% img http://i.imgur.com/qAV0N2e.png %}

Bila sudah menemukan partisi OS kita, selanjutnya kita akan memount partisi tersebut. Ingat gantikan *sda5* dengan nama partisi anda.
``` bash
mount /dev/sda5 /mnt
```
Bila anda memiliki partisi */boot* yang terpisah, anda perlu juga memount partisi itu (misalnya sda6).
``` bash
mount /dev/sda6 /mnt/boot
```
Anda perlu juga memount filesystem yang penting.
``` bash
mount --bind /dev  /mnt/dev
mount --bind /dev/pts  /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys  /mnt/sys
```
Setelah itu kita akan melakukan chroot ke OS kita yang seharusnya.
``` bash
chroot /mnt
```

Langkah selanjutnya sangat penting, yaitu melakukan update-grub, sebaiknya lakukan saja hal ini, karena mungkin file */boot/grub/grub.cfg* biarpun ada, tapi sudah tidak sesuai.
``` bash
update-grub
```
Sampai disini, saya coba merestart komputer saya, dan hasilnya, saya masuk ke tampilan comman line grub, tidak lagi bootloop, tapi berarti masih ada yang kurang dan belum benar, karena itu kita perlu melakukan install ulang grub.
``` bash
grub-install /dev/sda 
grub-install --recheck /dev/sda 	
```
Perhatikan disini saya menggunakan */dev/sda* saja bukannya *sda5*, sesuaikan dengan nama drive anda. Command kedua hanya untuk verifikasi saja. Bila tidak ada error, sebenarnya sudah selesai, anda hanya perlu melakukan unmount terhadap semua file yang kita mount tadi dan restart komputer untuk kemudian masuk ke Grub yang sudah kembali benar.
``` bash
umount /mnt/dev/pts
umount /mnt/dev
umount /mnt/proc
umount /mnt/sys 
umount /mnt/boot
umount /mnt
reboot
```

Referensi :

- <http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/>
- <http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows>
- <http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/>
- <http://ubuntuforums.org/showthread.php?t=1916698>
- <http://askubuntu.com/questions/32135/stuck-on-grub-command-line>
- <https://help.ubuntu.com/community/Grub2>