---
title: "Error Eclipse"
date: 2012-09-28 18:34
categories: [eclipse, ubuntu, error]
---

Saya betul-betul dalam kebingungan untuk menentukan editor atau IDE apa yang akan saya gunakan dalam development aplikasi. Saya sudah dari dulu mencari IDE untuk Ruby on Rails di Linux, dan akhirnya dari dulu saya kembali memilih Gedit dengan rangkaian pluginnya sebagai editor Rails utama. Sementara untuk Android saya sudah pasti tidak bisa berpindah dari Eclipse, sudah nyaman dan cukup terbiasa dengan interfacenya.

Dari hasil pencarian di Google saya menemukan plugin rails untuk Eclipse dari Aptana, di OS Windows saya menggunakan Aptana Studio sebagai IDE dan cukup suka meskipun berasa sangat berat. Dengan plugin ini saya harap akan mendapatkan kebaikan dari Aptana dengan interface Eclipse.
<!--more-->
Saya segera membuka Eclipse saya, dan ternyata saya mengalami error, Eclipse tidak mau terbuka dan mengatakan bahwa sudah menulis log di dalam folder .metadata di workspace. Saya segera menuju file log tersebut dan ternyata error yang muncul di sekitar ObjectNotFoundException dari saran di situs StackOverflow saya kemudian mendelete folder .metadata dengan resiko kehilangan seluruh project saya (bukan file project, hanya settingan project, sehingga project tidak tertampil di Eclipse). Kemudian saya restar Eclipse dan memang Eclipse berjalan kembali, bisa masuk workspace saya yang sekarang tampak kosong tanpa project satupun (--__--).

Tapi belum selesai disitu kemudian muncul error lagi, sekarang di bagian console Eclipse yang menyatakan error berhubungan dengan ADT atau Android plugin. Saya segera browsing lagi dan ternyata memang permasalahan yang umum. Bisa diselesaikan dengan menginstall ulang beberapa lib, katanya error kedua ini muncul karena ADT dibuat untuk sistem 32 bit tapi untungnya Ubuntu bisa mengatur agar program di OS 64bit menggunakan lib untuk 32bit.
		apt-get install lib32ncurses5 lib32stdc++6 #ini yang singkat dan tepat
		apt-get install ia32-libs #ini versi download semua (40libs ~ 240mb)

Untuk mempelajari lebih lanjut mengenai troubleshooting error Eclipse bisa dilihat di link paling bawah dari daftar link yang membantu saya dalam memecahkan masalah ini.

1. <http://stackoverflow.com/questions/10005907/eclipse-android-plugin-libncurses-so-5>
2. <http://askubuntu.com/questions/147400/problems-with-eclipse-and-android-sdk>
3. <http://stackoverflow.com/questions/3505187/eclipse-galileo-wont-start-error-objectnotfoundexception-tree-element>
4. <http://www.eclipsezone.com/eclipse/forums/t99010.html>
