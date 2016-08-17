---
title: "Enable Hibernate Ubuntu 12.04"
date: 2012-10-02 20:42
categories: [ubuntu, hibernate]
---
Sewaktu pertama kali menginstall Ubuntu 12.04 di laptop Thinkpad T400 ini langsung terlihat satu hal yang aneh. Yaitu terlihat bahwa menu untuk Hibernate di-disable di deretan Shutdown, Suspend, Log Out dan lain-lain. Saya bingung tapi kemudian memutuskan untuk membiarkan saja dahulu, karena ada beberapa hal lain yang terasa lebih penting untuk di setting terlebih dahulu.
<!--more-->
Waktu berjalan dan Thinkpad saya sudah layak digunakan untuk melakukan berbagai kegiatan dan pekerjaan saya. Mulailah saya terganggu lagi dengan tidak adanya fungsi Hibernate ini di Ubuntu, karena kebiasaan saya tidak langsung menyelesaikan satu pekerjaan, tetapi mengerjakan beberapa sekaligus, sehingga mengakibatkan di satu waktu, saat harus pergi atau ada urusan lain, saya harus sebal karena terpaksa mematikan laptop dan merelakan berpuluh-puluh tab browser, text editor, program, terminal harus ditutup dan membuka kembali saat akan menggunakan lagi nanti. Ada opsi Suspend sebenarnya, tapi saya tidak merasa aman, membawa laptop dengan kondisi menyala seperti itu berjalan kemana-kemana.

Akar Masalah
Saya putuskan harus segera menyelesaikan masalah yang terlihat sepele tapi mengganggu ini. Dengan browsing singkat langsung bisa ditemukan sumber masalahnya. Karena seperti biasa, bukan cuma saya yang mengalami masalah seperti ini. Banyak juga orang yang mempertanyakan ketiadaan fungsi Hibernate secara default di Ubuntu 12.04 (padahal terlihat menunya, tapi di-disable). Dari halaman search Google, saya pilih tiga link yang terlihat paling layak.

Jadi memang Hibernate secara default di-disable dari menu Ubuntu 12.04. Karena dilaporkan banyak ketidaksesuaian, ketidakkompatibilatasan program dengan sistem hibernate yang dapat menyebabkan berbagai macam error. Tapi bagaimanapun tetap diberikan cara untuk membuatnya jadi bisa dilakukan, dan disarankan hanya dilakukan oleh user yang sudah berpengalaman dan mengetahui apa yang akan mereka lakukan terhadap sistemnya. Baiknya bahkan mencoba terlebih dahulu untuk melakukan hibernate dari command terminal, karena command ini tidak di-disable sebenarnya, masih bisa dilakukan. Bila hibernasi berhasil dilakukan dengan command dari terminal ini, maka mungkin bisa mulai memikirkan untuk re-enable Hibernate dari menu Ubuntu 12.04.

Penyelesaian
* Pertama kali mari kita mengetes terlebih dahulu, apakah sistem kita bisa melakuakn hibernate dengan normal melalui command dari terminal.
		sudo pm-hibernate
* Bila setelah itu ternyata hibernasi berjalan dengan baik, maka mari kita lanjutkan untuk mengedit agar menu Hibernate bisa diakses lagi.
		sudo nano /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
* Kemudian isilah dengan script berikut :
		[Re-enable hibernate by default]
		Identity=unix-user:*
		Action=org.freedesktop.upower.hibernate
		ResultActive=yes
Restart atau lakukan Log Out dan Hibernate akan bisa langsung diakses dari menu di atas kanan Ubuntu seperti biasanya dulu.
Menurut saya karena memang oleh Developer Ubuntu menu ini di-disable secara default, maka kita harus benar-benar mengetesnya juga, jangan sampai justru membuat sistem kita menjadi tidak stabil. Dari pengalaman saya setelah me-re-enable Hibernate tidak ada masalah yang terjadi, semuanya berjalan lancar dan tidak ada gangguan. Selamat mencoba.
---
Tinjauan
---
1. <http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/>
2. <http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04>
3. <http://askubuntu.com/questions/111669/hibernate-missing-from-power-menu-and-when-i-press-laptop-power-button>
