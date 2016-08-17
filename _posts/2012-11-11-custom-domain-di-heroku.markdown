---
title: "Custom Domain di Heroku"
date: 2012-11-11 23:14
categories: [blog, heroku, octopress, domain name, zerigo dns]
---
Saat membuat blog ini saya mengalami sedikit kesulitan sewaktu akan menggunakan Custom Domain di [Heroku][]. Dari beberapa artikel yang saya temukan di Google, Heroku mendukung custom domain dan terlihat mudah saat konfigurasinya. Saya kemudian membeli domain dari [e-Padi.com][], prosesnya agak lama, sepertinya sedang ada gangguan di sistem mereka sehingga saya terpaksa menunggu beberapa hari sebelum bisa menggunakan domain saya, itupun setelah berkali-kali menghubungi lewat beberapa media, chat YM dan SMS.
<!--more-->
Setelah berhasil mengaktifkan domain, saya langsung masuk ke dashboard, baik untuk [e-Padi.com][] dan [Heroku][]. Di [Heroku][] saya mengaktifkan Add On Custom Domain, sementara di [e-Padi.com][] saya mencari lokasi setting name server. Dari [petunjuk di Heroku][1] tampak sangat mudah untuk setting Custom Domain ini, tapi pada kenyataannya saya gagal pada percobaan pertama karena bingung saat akan setting name server di [e-Padi.com][].

Setelah beberapa saat bingung, saya kemudian memutuskan mencoba add on [Zerigo DNS][]. Untuk menggunakan add on di [Heroku][] kita diharuskan melakukan verifikasi account dengan memasukkan data kartu kredit yang valid, pastikan untuk melakukan verifikasi ini terlebih dahulu, karena langkah penggunaan add on tidak akan bisa dilakukan.

Kemudahannya luar biasa saat melakukan setting dengan [Zerigo DNS][] dan memasukkan ke [e-Padi,com][]. Cukup instalasi add on, setting domain yang akan kita pakai, dan kemudian dilanjutkan dengan memasukkan konfigurasi [Zerigo DNS Server][] ke panel setting [e-Padi.com][].

Berikut langkah-langkahnya :

1. Verifikasi account anda di interface web [Heroku][].
2. Install add on [Zerigo DNS][]
		$ heroku addons:add zerigo_dns:basic
		Installing zerigo_dns:basic into myapp...done.
3. Setting Zerigo DNS server ke panel setting domain manajemen anda
		a.ns.zerigo.net
		b.ns.zerigo.net
		c.ns.zerigo.net
		d.ns.zerigo.net
		e.ns.zerigo.net
4. Tambahkan domain yang anda miliki ke [Heroku][], bila anda sebelumnya sudah mengintall add on Custom Domain dan sudah menambahkan Custom Domain, konfigurasi tersebut otomatis akan ditambahkan ke sistem [Zerigo DNS][]
		heroku domains:add mydomain.com
5. Sudah selesai, bisa membutuhkan waktu sekitar 1 hari untuk setting ini bisa berjalan penuh (pengalaman saya bahkan sekitar 2 hari). Bisa dicek dengan perintah host di Linux.
		$ host www.johannesdwicahyo.com
		www.johannesdwicahyo.com is an alias for proxy.heroku.com.
		proxy.heroku.com has address 107.21.95.3
		proxy.heroku.com has address 174.129.23.129
		proxy.heroku.com has address 50.16.215.20
		proxy.heroku.com has address 50.16.215.41
		
Selamat mencoba, silahkan menambahkan pengalaman dan temuan anda di kolom komentar. :)

[1]: https://devcenter.heroku.com/articles/custom-domains
[Heroku]: http://www.heroku.com
[Zerigo DNS]: https://devcenter.heroku.com/articles/zerigo_dns
[e-Padi.com]: http://www.e-padi.com
[Zerigo DNS Server]: https://devcenter.heroku.com/x?url=http%3A%2F%2Fwww.zerigo.com%2Fmanaged-dns%2Ftechnical_specs


