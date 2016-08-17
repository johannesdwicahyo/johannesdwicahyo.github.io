---
title: "Misteri Ubuntu"
date: 2012-09-22 10:16
categories: [ubuntu, kaskus, root]
---

Sempat terpukau sesaat kemarin saat membaca salah satu diskusi di Forum Komputer Kaskus, di sub forum Linux dan OS selain Microsoft dan Mac. Ada diskusi yang awalnya saya kira sederhana mengenai kasus yang tampaknya sederhana di Ubuntu. Saya yang bertahun-tahun menggunakan Ubuntu pun tidak pernah memikirkannya dan mengangapnya sebagai hal yang sederhana, tidak menganggap rumit sama sekali, tetapi saat membaca diskusi halaman pertama saya jadi ragu dengan pemikiran sederhana saya, rasanya saya jadi tidak bisa menjawab pertanyaan yang didiskusikan disitu dan semakin merasa kalau saya begitu dangkalnya selama ini dalam mengenal Ubuntu.

Silahkan lihat pertanyaan lengkapnya disini <http://www.kaskus.us/showthread.php?t=3467589>.
<!--more-->

> Intinya user ini mempertanyakan saat kita menginstal Ubuntu, kita tidak diberi pertanyaan untuk memasukkan password ROOT, tapi disuruh membuat user dan password untuk user tersebut. Tapi kemudian kita bisa mengakses command yang seharusnya hanya bisa dilakukan oleh root dengan SUDO, {"jadi apakah sebenarnya ROOT di Ubuntu itu?"} apa hubungannya dengan user yang kita buat saat install?

Ini screen shoot dari pertanyaan lengkapnya.

{% img http://1.bp.blogspot.com/-58pg9mgcrcE/T8XUxl2-R9I/AAAAAAAAARo/_QOzltbumWA/s1600/ubuntu-kaskus.PNG %}

Dari pertanyaan yang awalnya tampak sederhana ini muncullah suatu diskusi yang alot dan tampak sama sekali belum terjawab dan jelas.

Pendapat awal yang muncul adalah dari agan kim-kim :

    Defaultnya, user lw ma root satu grup ma sebuah grup yang bernama root. Jadi, sebuah user akan menaikkan akses dari owner ke grup dengan cara memasukkan password.
    Nah makanya lw kudu masukin pass bwt akses ke root karena lw root adalah pemilik command tersebut dan lw satu grup ma dia...

Kemudian di-amin-i oleh beberapa user lain, karena dianggap cukup logis dan bisa diterima. bahkan didukung oleh agan wupz :

    Ubuntu secara default memang begitu. User yang dicreate pertama kali saat installasi akan masuk ke group admin, dimana member dari group ini bisa menggunakan perintah sudo (menjalankan perintah sebagai root CMIIW). Dan value dari password root adalah kosong (no password) yang tentu saja secara default user tidak bisa login dengan id root CMIIW. Sehingga dalam hal ini, user memang tidak bisa login dengan id root, dimana memang itu sangat berbahaya.
    Jika Anda bikin user lagi, dan tidak di add ke group admin, dia tidak bisa menggunakan perintah sudo.

Tapi oleh bung TS yang nampak kurang puas, diperdalam lagi pertanyaan itu. Berarti dengan begitu keadaannya, Ubuntu akan mirip seperti Windows dengan Administratornya dan betapa tidak hebatnya ROOT yang berarti bisa dibuatkan passwordnya oleh user biasa.

Kemudian di page 2 agan mango muncul dengan mantapnya, dan kemudian menjelaskan dengan cukup sangat jelas.

    @ts dan yang lain

    kesampingkan dulu semua asumsi dan pengetahuan soal root, sudo, dan user saya. Informasi yang gue kasih mungkin ngga 100% bener, tapi jangan takut,

    gue bakal bilang gue sendiri ngga yakin kalo gue ngga yakin.

    Gue lurusin beberapa hal dulu ya, dari yang paling basic.

    1. Pada semua distribusi linux (dan varian unix) ada dua tipe user : "superuser" dan "(normal) user"

    2. Yang termasuk kedalam tipe "superuser" (biasanya) adalah root, dan yang termasuk kepada tipe "(normal) user" ya user yang ngga punya root privileges (misal, user "saya")

    Persoalan user dan group dan file permission/privileges

    3. Kalau kita ngomongin soal file privileges, kita juga bicara soal

    "user" dan "group". "user" dan "group" disini jangan dihubungin dengan tipe "superuser" dan "(normal) user" di poin gue yang ke-1 dan 2

    4. Pada semua distribusi linux (dan varian unix), sebuah file dimiliki oleh satu orang user dan satu group

    5. Ketika seorang user (misal: user "saya") dibuat oleh superuser, maka secara otomatis user "saya" dan group "saya" dibuat

    6. Seorang user hanya bisa melakukan execute dan/atau read dan/atau write pada file user tersebut

    7. Seorang user bisa "bergabung" ke dalam sebuah group atas seizin superuser

    8. Seorang user yang telah bergabung kedalam group tertentu bisa

    melakukan execute dan/atau read dan/atau write pada file yang dimiliki oleh group tersebut

    9. Untuk mengubah kepemilikan sebuah file untuk seorang user dilakukan dengan perintah chown (sebagai superuser)

    10. Untuk mengubah kepemilikan sebuah file untuk sebuah group dilakukan dengan perintah chgrp (sebagai superuser)

    Soal su

    11. Su adalah sebuah program yang mengizinkan seorang user untuk menjadi user lain (termasuk sebagai superuser) didalam login sessionnya (baca: setelah user tersebut login, baru bisa mengeksekusi perintah su sebagai user lain)

    12. Ketika user mengetikkan perintah su dan diminta password, maka password yang diminta adalah password dari user yang ia ingin jadikan (misal password root atau password user lain)

    Soal sudo

    13. Sudo adalah sebuah program yang mengizinkan seorang user untuk mengeksekusi perintah sebagai user lain, termasuk sebagai superuser

    14. Perintah-perintah apa saja yang bisa dieksekusi dan atas user siapakah perintah itu dijalankan, diatur dalam sudoers file (/etc/sudoers pada ubuntu)

    15. Ketika user mengetikkan perintah sudo dan diminta password, maka password yang diminta bukanlah password user yang akan mengeksekusi perintah tersebut (misal, password root), melainkan password user itu sendiri (misal, password user "saya"). Beda dengan su (liat #12)

    16. Session pada sudo bisa expired. Pada Ubuntu (kalo ngga salah) diset secara default selama 15 menit. Setelah itu password harus dimasukkan lagi

    Soal spesifik pada Ubuntu

    17. Secara default, superuser "root" pada Ubuntu di-lock. Dalam artian, root sama sekali tidak bisa login, tapi usernya tetap eksis. Passwordnya bukan kosong.

    18. Setelah pertama kali install Ubuntu, seorang user dibuat (misal, user "saya"). User ini secara otomatis di-assign sebagai "System administrator"

    19. User selanjutnya yang dibuat melalui "System-&gt;Administration-&gt;Users and Groups" secara default ngga akan jadi "System administrator" kecuali opsi "Administer the system" dicentang

    20. Definisi dari "System administrator" pada Ubuntu (inget, bukan pada distro atau varian unix lain) adalah: User yang bisa menjalankan semua perintah root melalui sudo (sebagai root, poin #13)

    21. Root pada Ubuntu bisa di-enable dengan :

    Code:

    $ sudo -i

    $ sudo passwd root

    Dengan gitu password root telah diset.

    22. Root pada Ubuntu yang telah di-enable bisa di-disable/lock lagi dengan:

    Code:

    $ sudo usermod -p '!' root

    Sudo dan Su

    23. Model security dari sudo dan su pada dasarnya sama. Kalo pada su securitynya bisa ditembus, begitu juga dengan sudo dan sebaliknya.

    Keuntungan Sudo

    24. User ngga perlu lagi nginget password dari root, soalnya biasanya kelupaan.

    25. Setiap command sudo yang dieksekusi, ada lognya di /var/log/auth.log =&gt; buat audit security dan buat rollback

    26. Hacker biasanya brute-force password root, karena pada Ubuntu root sama sekalo ngga bisa login sebelum di-enable dan passwordnya diset (poin #21), maka brute-force sama aja boong kalo ngga tau user mana yang bisa execute sudo sebagai user.

    27. Mudah transfer root privileges dari satu user ke user yang lain (poin #19) tanpa harus share password root dengan administrator lain

    28. Session sudo timeout setelah jangka waktu tertentu (poin #16)

    29. Sudo sangat fine-grained, hanya perintah-perintah yang didefinisikan di file sudoers saja yang bisa dijalankan. Berguna kalau misal kita ingin membuat user lain sebagai "system adminisrator" pada ubuntu tapi tidak mengizinkan perintah "shutdown" untuk dieksekusi.

    Kerugian Sudo

    29. sudo echo "foo" &gt; /root/foo.txt misalnya ngga bisa jalan karena pada dasarnya shell/terminal yang dijalankan dengan user id kita yang mencoba untuk menulis file /root/foo.txt. Bisa diakalin pakai sudo "tee"

    Semoga penjelasan gue cukup mudah untuk dimengerti buat semuanya. Tanya aja kalo ada yang ngga ngerti atau kalo ada yang salah 

Mantap penjelasannya. Langsung dengan poin-poin yang jelas sekali. Dan diskusi ini pun berakhir dengan kejelasan yang pasti, seingat saya semua pihak puas, saling mendapatkan hal yang berguna bagi masing-masing.

Sebenarnya kalau mau tahu jawabannya sudah ada dari page 1, di link di Ubuntu Help dari agan orccha. Silahkan kalau mau penjelasan lebih lengkap tapi dalam bahasa inggris bisa mengunjungi [link ini][1].

[1]: https://help.ubuntu.com/community/RootSudo


