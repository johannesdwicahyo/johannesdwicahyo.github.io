---
title: "Tidak Bisa Update Ubuntu Gara-gara XL"
date: 2013-04-30 13:32
categories: ubuntu, provider, internet, update, apt-get, error 403
---

Biarpun masalah ini sudah selesai mulai bulan ini, saya tetap merasa tidak ada salahnya untuk menuliskannya, karena sempat membuat saya bingung dan kerepotan seharian. Ubuntu saya yang seperti biasa akan mengecek update bila terhubung dengan jaringan internet mengatakan bahawa ada update yang bisa saya install. Setelah saya klik tombol untuk mengupdate, memasukkan password, tiba-tiba muncul error 403. Kenapa ini?
<!--more-->
{% img http://i41.tinypic.com/6gluzl.png %}
{% img http://i40.tinypic.com/2zq77ls.png %}
{% img http://i40.tinypic.com/14lh9us.png %}
{% img http://i44.tinypic.com/swefiv.png %}

Saya googling cukup lama mengenai masalah ini, dan seperti biasa, masalah ini merupakan masalah banyak orang juga di seluruh dunia, dan banyak orang yang sudah berbagi berbagai troubleshooting untuk mengatasi masalah ini. Silahkan di [search juga di google][1].

Hal pertama yang saya cek adalah jaringan XL, sebagai provider yang saat itu saya pakai. Saya memiliki dua sumber internet sebenarnya, pertama adalah modem Smartfren dengan Kuota 3Gb perbulan dan XL Hotrod 3G dengan kuota 1,5Gb perbulan, karena saat itu kuota Smartfren sudah habis, jadi saya hanya memiliki koneksi melalui XL Hotrod 3G. Saat saya gunakan untuk browsing, buffering video, baca komik dan mendownload file, tidak ada masalah apa-apa, saya cek kuota juga masih cukup, saya putuskan masalah bukan di jaringan internet XL.

Kemudian saya cek sources.list saya. Saat menggunakan Ubuntu Software Center, saya bahkan masih bisa melakukan pemilihan source dengan kecepatan paling baik, yang kemudian saya gunakan untuk menggantikan source yang saat ini saya gunakan. Karena curiga juga error disebabkan oleh tambahan-tambahn ppa, saya hapus juga ppa yang ada, sehingga hanya menggunakan source standar. Dan hasilnya saya masih gagal melakukan update.

Bila anda mencari dari internet akan banyak sekali juga cara yang disarankan untuk menyelesaikan error ini, hampir semuanya saya coba, dan saya masih gagal, saya sampai browsing di halaman kedua hasil search dan seterusnya, mengganti dengan berbagai macam keyword yang mungkin bisa berhasil. Dan hasilnya saya masih gagal juga.

Saya putuskan untuk menyerah dulu di hari itu, toh saya belum terlalu butuh update dan dengan tidak mengupdate software pun Ubuntu saya masih berjalan. Tetapi hal ini hanya berjalan beberapa hari, saya kemudian butuh untuk menginstall software baru dan mengalami error juga pastinya untuk instalasinya. Jadilah saya kembali berkutat mencari solusi untuk masalah ini.

Pada akhirnya, saya browsing ke banyak sekali halaman yang terhubung dengan hasil pencarian, dan menemukan satu artikel yang berbeda, artikel ini bercerita mengenai masalah update saat menggunakan jaringan internet tertentu, kasus ini terjadi di luar negeri, ternyata itu memang merupakan policy dari penyedia internet untuk memblok akses terhadap beberapa jenis situs. Dari situ saya berpikir, jangan-jangan ini juga karena XL-nya. Kemudian saya isi pulsa Smartfren, ubah koneksi ke modem Smart dan mencoba lagi untuk update. Hasilnya, saya sukses melakukan update, tidak ada masalah apapun, update selesai tanpa error, kemudian saya juga bisa menginstall software yang saya butuhkan tadi.

Akhirnya diketahui masalah ada pada jaringan XL Hotrod, untuk sekarang untungnya error ini sudah tidak terjadi. XL Hotrod saya sudah bisa lagi digunakan untuk update Ubuntu, semoga untuk selamanya bisa seperti ini sehingga saya tidak perlu repot lagi mengganti koneksi saat ingin menginstall software tapi menggunakan XL.

**Update**

*Error lagi hari ini, sepertinya memang ada yang salah dari jaringan XL, mungkin ada batasan jaringan dengan kuota tertentu, nanti saya coba follow up ke Xl kalau tidak malas..

[1]: https://www.google.com/search?client=ubuntu&channel=fs&q=error+403+update+ubuntu&ie=utf-8&oe=utf-8