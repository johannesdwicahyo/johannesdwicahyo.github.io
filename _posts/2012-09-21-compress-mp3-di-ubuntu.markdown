---
title: "Compress MP3 di Ubuntu"
date: 2012-09-21 23:23
categories: [ubuntu, bash, shell, mp3, compress, script]
---

Saya masih ingat kira-kira di tahun 2006-2007, saya masih mempunyai ( sebenarnya dipinjami oleh teman, tapi akhirnya diakuisisi jadi milik pribadi ) sebuah mp3 player kecil, mereknya Dolphin kalau tidak salah, berwarna hitam dengan memory 256mb. Kecil sekali ya kalau dibandingkan dengan produk-produk jaman sekarang, tapi seingat saya pada waktu itu memory segitu masih cukup lumayan.
<!--more-->
Tapi tetap saja, biarpun masih "lumayan", saya tetap merasa butuh memasukkan lebih banyak lagi mp3 kedalam player tersebut. Pastinya yang terpikir adalah bagaimana membuat file mp3 menjadi berukuran lebih kecil dari normal di kisaran 4-6 mb perfile menjadi sekitar 1-3mb perfile.

Di windows saya biasa menggunakan software dbPowerAmp untuk melakukan compress file mp3, tapi di linux saya belum menemukan program sejenis waktu itu. Jadi saya berusahan mencari cara agar bisa melakukan compress mp3 di Ubuntu.

Setelah googling sesaat, terlihat titik cerah untuk melakukan hal ini, ternyata cukup dilakukan dengan script sederhana dan memastikan LAME terinstall di komputer kita.

Langkah-langkah yang saya lakukan :

* Memastikan LAME telah terinstall, bila belum silahkan install dengan software package management kesukaan anda
* Letakkan mp3 yang akan di compress ke dalam satu folder, misalnya folder bernama mp3, dengan terminal masuk ke folder itu.
* Buat file baru di dalam folder itu, misalnya dengan nama compress.sh dan masukkan kode berikut sebagai isinya
			
			{% highlight bash %}
			mkdir ./compressed
			for file in *.mp3; do lame --mp3input -b 32 "$file" "./compressed/$file"; done
			{% endhighlight %}
* Ubah akses file compress.sh agar bisa dieksekusi
			
			{% highlight bash %}
			chmod ugo+x compress.sh
			{% endhighlight %}
* Jalankan file compress.sh

			{% highlight bash %}
			./compress.sh
			{% endhighlight %}
* MP3 yang terkompress sudah ada di folder compressed dan jelas memiliki ukuran file yang lebih kecil.

Disini saya mengubah bitrate mp3 menjadi 32kbps,bila menginginkan kualitas yang lebih baik, bisa menggunakan angka yang lebih tinggi, bitrate normal biasanya 128-192kbps, silahkan coba-coba mana yang paling sesuai untuk anda.

Menurut saya, secara kualitas suara, hasil compress mp3 dengan cara ini jauh lebih baik daripada menggunakan dbPowerAmp atau software sejenis di Windows. Silahkan dibuktikan ;)
