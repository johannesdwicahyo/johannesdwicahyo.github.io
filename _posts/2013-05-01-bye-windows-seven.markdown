---
title: "Bye Windows Seven"
date: 2013-05-01 15:25
categories: windows, move on, linux, ubuntu, uninstall
---

Hari ini saya membuat keputusan yang sudah lama saya tunda, yaitu untuk menghapus sama sekali OS Windows dari laptop saya dan bergantung sepenuhnya dengan Ubuntu sebagai OS satu-satunya (selain yang virtual :D).
<!--more-->
Ada beberapa cara untuk menghapus Windows yang sebelumnya di dualboot dengan Ubuntu. Paling tidak ada dua cara secara garis besar, cara repot dengan manual melakukan penghapusan lewat beberapa tools dan cara ringkas, cukup dengan beberapa kali klik, windows akan teruninstall.

Cara repot dimulai dengan booting live CD, atau bisa juga langsung menggunakan GParted live CD, karena kita akan menggunakan Gparted sebagai langkah awal.

Kemudian setelah Gparted berhasil dijalankan, kita harus menemukan manakah yang merupakan partisi milik OS Windows diinstall, bisa dikenali dengan mudah karena biasanya memiliki tipe NTFS dan terdapat bootflag.

Setelah yakin bahwa itu merupakan partisi yang benar, mari kita hapus partisi berikut. Dapat dilanjutkan juga langsung dengan menggunakan partisi kosong itu sebagai partisi lain yang akan lebih berguna bagi kita.

Langkah selanjutnya berhubungan dengan Grub. Bila anda tadi setelah menghapus partisi Windows kemudian melakukan restart komputer, anda akan mengalami error karena Grub belum disetting untuk menuju OS Ubuntu secara langsung. Karena saya malas menulisnya silahkan langsung menuju [situs Ubuntu][1] untuk melihat secara lengkap kelanjutan cara repot ini.

Saya sarankan untuk menggunakan [cara ringkas][2], yaitu menggunakan OS-Uninstaller. Dengan beberapa klik anda sudah dapat memperoleh hasil yang sama. Pertama-tama tentu saja mengunduh dan menginstall software OS-Uninstaller.
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update; sudo apt-get install -y os-uninstaller && os-uninstaller
```
Setelah proses instalasi selesai, OS-Uninstaller langsung berjalan dengan sendirinya, melakukan scanning, OS apa saja yang terdapat di komputer kita, kemudian memunculkan window sederhana untuk memilih OS apa yang akan kita hapus.
{% img http://pix.toile-libre.org/upload/original/1323945652.png %}
Setelah menentukan OS mana yang akan kita hapus, kita klik OK dan akan muncul halaman konfirmasi.
{% img http://pix.toile-libre.org/upload/original/1336577243.png %}
Setelah melakukan konfirmasi, proses akan berjalan dan setelah beberapa saat akan muncul notifikasi yang memberikan kabar gembira bahwa OS yang ingin kita hapus sudah berhasil di hapus.

[1]: https://help.ubuntu.com/community/HowToRemoveWindows
[2]: https://help.ubuntu.com/community/OS-Uninstaller