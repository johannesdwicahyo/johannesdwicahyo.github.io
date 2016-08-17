---
title: "Instal Conky di Ubuntu"
date: 2012-09-22 08:22
categories: [ubuntu, conky]
---

Dulu sebenarnya saya sudah pernah sukses menginstall Conky di Ubuntu, dan sekarang saya mau mengulanginya. Untuk anda yang belum tahu Conky merupakan aplikasi yang mirip seperti Rainmeter di Windows platform. Conky bisa membantu menunjukkan keadaan sistem kita seperti apa, seperti CPU load, memory usage, network connection sampai email maupun RSS reader dengan tampilan yang bisa dikonfigurasi dengan leluasa.
<!--more-->
Conky seperti juga RainMeter memiliki pengaturan yang sangat luas, dan jangan dikira karena Conky hanya untuk platform Linux maka tampilannya akan kalah jauh dengan RainMeter, harus saya akui hal itu tidak berlaku sama sekali, sudah banyak contoh konfigurasi Conky yang luar biasa indah dan sama sekali tidak kalah dari RainMeter.

Untuk instalasinya cukup mudah, saya memilih menggunakan instalasi ConkyColors yang disebut-sebut dapat memudahkan konfigurasi Conky. Saya mengkuti tutorial dari [sini][1]. Instalasi berjalan lancar sampai ke step untuk memulai Conky saya ketikkan persis seperti di petunjuk itu, tapi terjadi error yang menyatakan bahwa theme tidak ditemukan. Kemudian saya edit untuk tidak menggunakan pilihan Theme, dan Conky sudah berjalan di laptop Ubuntu 11.04 saya. Dan bahkan untuk memassukan ke startup application akhirnya saya tidak mengikuti petunjuk tetapi mengarahkan langsung ke file binary dari Conky, tidak melalui ConkyColors.

Tampilan yang saya peroleh awalnya kurang memuaskan. Saya kurang tahu dan karena sedang tidak ada waktu untuk mencari tahu saya akhirnya memilih mengganti langsung konfigurasi Conky saya di ~/.conkyrc. Saya ganti dengan script yang saya temukan dari hasil browsing tentang contoh konfigurasi Conky, dan paling tidak hasilnya sekarang lebih baik dari tadi.

[1]: http://helmuthdu.deviantart.com/art/CONKY-Colors-244793180
