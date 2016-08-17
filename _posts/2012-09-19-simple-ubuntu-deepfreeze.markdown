---
title: "Simple Ubuntu DeepFreeze"
date: 2012-09-19 19:05
categories: [ubuntu, deepfreeze, script, bash]
---
Salah satu request awal dari Laboran di lab komputer saya adalah program seperti Deep Freeze yang bisa berjalan di linux. Hal ini dibutuhkan karena lab komputer kami juga sekaligus berfungsi seperti warnet di kampus, jadi untuk menghindari kerusakan karena kesalahan penggunaan user, selama ini di Windows kami menggunakan Deep Freeze, jadi setiap komputer di restart, akan kembali ke setting seperti semula.
<!--more-->
Sewaktu itu jelas belum ada software yang bisa melakukan fungsi selengkap deep freeze pada linux ubuntu, tetapi dari trainer kami dijanjikan akan dibuatkan script untuk dapat melakukan fungsi tersebut.

Jadi dari rencana yang kami buat bersama, user akan dibuat dengan otoritas seminimal mungkin, tanpa hak instalasi dan terbatas akses terhadap home foldernya sendiri. Untuk mempertahankan fase/memiliki tampilan standar sebenarnya secara sederhana yang perlu dilakukan adalah memiliki backup dari home folder user dan meng-copy-kan backup tersebut setiap komputer startup.

Dan akhirnya langkah-langkah yang kami lakukan :

* Membuat backup home folder user, dilakukan dengan menggunakan login root, karena kami mau menempatkan backup foldernya di folder /root, dapat dilakukan melalui file explorer (nautilus) ataupun melalui syntax di terminal (copy -R)
* Membuat script untuk mengcopy folder tersebut
		
		{% highlight bash %}
		rm -rf /home/user
		cp -arf /root/user /home/
		chown -R user:user /home/user
		{% endhighlight %}
* Misalnya kemudian kita beri nama freeze.sh, lalu dengan terminal ubah aksesnya dengan chmod, agar bisa dieksekusi sebagai script maka ketikkan perintah
		
		{% highlight bash %}
		chmod ugo+x freeze.sh
		{% endhighlight %}
* Selanjutnya adalah membuat agar script ini bisa berjalan secara otomatis ketika startup, edit file rc.local
		
		{% highlight bash %}
		nano /etc/rc.local 
		#Tambahkan kode ini di bagian akhir file, kemudian save.
		/root/freeze.sh
		{% endhighlight %}

Seharusnya script "Deep Freeze" sangat sederhana ini sudah bisa berjalan, paling tidak bisa mengembalikan settingan standar dari software yang baru saja digunakan, wallpaper dan berbagai tampilan desktop lainnya.

Untuk penjelasan scriptnya saya rasa scriptnya sangat mudah dan sederhana, silahkan ditanyakan bila ada yang tidak mengerti. :) 
