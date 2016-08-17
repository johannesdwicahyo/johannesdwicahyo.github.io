---
title: "Instalasi Metasploit di Ubuntu 11.04"
date: 2012-09-22 10:01
categories: [ubuntu, metasploit, install]
---

Saya kira anda sudah tahu tentang Metasploit bila sampai ke blog saya ini melalui search engine, jika belum maka anda dapat membaca <http://www.metasploit.com/> mengenai metasploit, mengenai fungsinya dan berbagai kemampuannya.

Instalasi Metasploit sebenarnya cukup mudah, hanya running install script dan mengikuti urutan langkah, dan akhirnya sedikit tambahan konfigurasi di akhir.
<!--more-->
Langkah-langkah yang saya lakukan :

* Download dari [url ini][1]. Pilih sistem operasi yang akan dipakai, untuk saya, saya memilih Linux 32bit. Untuk memudahkan juga bisa langsung gunakan wget untuk mendownload file tersebut.
		{% highlight bash %}
			wget http://downloads.metasploit.com/data/releases/metasploit-latest-linux-installer.run
		{% endhighlight %}
* Install dependency yang dibutuhkan, mungkin juga beberapa dependency ini sudah terpenuhi di machine anda.
		$ sudo apt-get install ruby libopenssl-ruby libyaml-ruby libdl-ruby libiconv-ruby libreadline-ruby irb ri rubygems
		$ sudo apt-get install subversion
		$ sudo apt-get install build-essential ruby-dev libpcap-dev
* Jalankan install script yang sudah anda download, sebelumnya buat agar file .run itu bisa dieksekusi.
		chmod ugo+x metasploit-latest-linux-installer.run
		./metasploit-latest-linux-installer.run
* Setelah ini instalasi selesai, anda sudah memiliki framework metasploit terinstall di komputer anda. Anda sudah bisa me-run msfconsole, tapi untuk fungsionalitas penuhnya kita perlu mensetting database.
Saya memilih PostgreSql, sesuai saran dari pembuat Metasploit juga.
		$ sudo apt-get install postgresql-8.4
		$ sudo apt-get install rubygems libpq-dev
		$ sudo gem install pg	
* Dilanjutkan dengan mensetting Postgre dan Metasploit
Di terminal pindah ke user Postgre
		$ sudo -s
		# su postgres Create Postgre User
		# createuser msf_user -P
* Anda akan mendapat prompt seperti ini
		Enter password for new role:
		Enter it again:
		Shall the new role be a superuser? (y/n) n
		Shall the new role be allowed to create databases? (y/n) n
		Shall the new role be allowed to create more new roles? (y/n) n
* Tentukan password untuk user anda, misalnya saya menggunakan password msfpass
Dan akhirnya buatlah database baru
		createdb --owner=msf_user msf_database
* Kemudian kembali ke user linux anda (ctrl-D), jalankan metasploit
		msf> db_driver postgresql
		msf> db_connect msf_user:msfpass@127.0.0.1:5432/msf_database
		msf> db_hosts

[1]: http://www.metasploit.com/download/
