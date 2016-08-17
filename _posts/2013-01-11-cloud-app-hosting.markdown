---
title: "Cloud App Hosting"
date: 2013-01-11 09:55
categories: Cloud, App Hosting, Heroku, Blog
---

[Google App Engine][1], [Amazon AWS][2], [Rackspace][3], [Heroku][4], [Bitnami][5], [Windows Azure][6].

Ini merupakan sedikit list dari sekian banyak penyedia layanan cloud application hosting, kebanyakan menyediakan free package untuk penggunaan standar, dengan tipe-tipe pembayaran sesuai dengan komponen yang dipakai. Mungkin penyedia awal yang pertama kali bermain di bidang ini adalah [Amazon][2], sudah sejak lama (tahun 2006) [Amazon][2] menyediakan layanannya, bahkan sebelum aplikasi [Cloud Computing][7] mulai seterkenal sekarang, sebelum menjadi tren.

<!--more-->

> Cloud computing is the use of computing resources (hardware and software) that are delivered as a service over a network (typically the Internet). The name comes from the use of a cloud-shaped symbol as an abstraction for the complex infrastructure it contains in system diagrams. Cloud computing entrusts remote services with a user's data, software and computation.

{% img http://upload.wikimedia.org/wikipedia/commons/thumb/b/b5/Cloud_computing.svg/400px-Cloud_computing.svg.png %}

Dengan skema [cloud computing][7], perusahaan atau developer diharapkan dapat berkonsentrasi lebih, menginvestasikan dana dan waktu yang lebih kepada hal-hal seperti bussiness process dan service development dengan mengesampingkan pembelian hardware, setting dan konfigurasi server, perencanaan upgrade hardware, scaling aplikasi dan hal-hal lain yang sudah disediakan oleh penyedia layanan cloud.

Sejujurnya, selama ini saya baru benar-benar pernah mencoba Cloud hosting di [Heroku][4], karena kemudahannya untuk hosting aplikasi yang rake based dan dari awal tahun 2012 sampai sekarang saya memang sedang banyak berkutat dengan aplikasi web berbasis Ruby, yaitu [Ruby on Rails][8] dan juga sekarang tambah menggunakan engine blog [Octopress][9] yang berbasis dari [Jekyll][10]. Biarpun sebenarnya saya juga sudah dari dulu memiliki account di penyedia layanan cloud hosting yang lain.

Faktor-faktor yang dapat mempengaruhi pemilihan cloud application hosting provider menurut saya berbeda antara pengguna Personal, Small/Home Bussiness dan Enterprise.

Kalau dari saya sebagai pengguna personal, misalnya untuk pemilihan saya terhadap Heroku sebagai provider hosting blog ini, faktor-faktor yang mempengaruhi antara lain :
1. Git-based, menggunakan [Git][11] untuk kontrol versi dan manajemen file, tinggal mensetting Git dan dapat dengan mudah menjaga versi aplikasi sekaligus mengupdate aplikasi live di Internet.
2. Gratis, saya menggunakan layanan free dari [Heroku][4], karena hanya untuk kebutuhan blog personal, dengan traffic yang sama sekali belum besar, saya sama sekali belum membutuhkan kemampuan computing yang tinggi, saya tidak memerlukan tambahan Dyno untuk aplikasi saya, dan bahkan saya tidak membutuhkan database, dengan minimal juga melakukan compiling halaman karena Octopress menggenerate static pages, dan inilah yang diakses oleh pengguna
3. Set-up mudah, [rake based][12], sangat mudah untuk deploy aplikasi rake di [Heroku][4], benar-benar hanya mem-push data melalui Git dan akan diproses dengan baik oleh [Heroku][4] menjadi aplikasi yang siap diakses
4. Banyak add-on, [Heroku][4] sudah menyediakan banyak [add-on][13] untuk melengkapi aplikasi kita dan banyak diantarnya juga free to use, mulai dari tools untuk manajemen domain, worker, scheduling dan bahkan Postgre Database bisa digunakan dan diinstall ke aplikasi kita dengan mudahnya

Sederhana sekali saya rasa kriteria yang saya butuhkan, dan karena semuanya dipenuhi dengan baik oleh [Heroku][4], maka tentu saja saya memilihnya. Untuk pemilihan bagi pengguna Small/Home Bussiness dan Enterprise, menurut saya yang perlu dipikirkan adalah mengenai keamanan jaringan, sertifikasi SSL, customer support, technical support, dukungan OS, dukungan platform, scalability dan tentu saja tidak bisa dilupakan efisiensi performa/harga, harus pintar-pintar melakukan komparasi harga antarprovider, bagaimana memperoleh layanan paling sesuai dengan budget yang tepat penggunaannya.

Further Reading :
1. <http://www.mrkirkland.com/cloud-computing-price-comparison/>
2. <http://sevcloud.blogspot.com/2010/05/cloud-hosting-price-comparison.html>
3. <http://cloud-computing.findthebest.com/>
4. <http://blog.assembla.com/assemblablog/tabid/12618/bid/9440/Cloud-hosting-providers-Compare-and-Contrast.aspx>
5. <http://www.antsmagazine.com/articles/10-valid-reasons-to-choose-cloud-hosting-for-your-business/>


[1]: https://cloud.google.com/products/?utm_source=google&utm_medium=cpc&utm_campaign=appengine-search
[2]: http://aws.amazon.com/application-hosting/
[3]: http://www.rackspace.com/cloud/saas/	
[4]: http://www.heroku.com/
[5]: http://bitnami.org/cloud	
[6]: http://www.windowsazure.com/en-us/
[7]: http://en.wikipedia.org/wiki/Cloud_computing
[8]: http://rubyonrails.org/
[9]: http://www.octopress.org
[10]: http://github.com/mojombo/jekyll
[11]: http://git-scm.com/
[12]: en.wikipedia.org/wiki/Rake_(software)
[13]: https://addons.heroku.com/
