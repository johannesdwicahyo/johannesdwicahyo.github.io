---
title: "Membuat Blog Dengan Octopress"
date: 2012-11-11 13:34
categories: [blog, ruby, octopress]
---

[Octopress][] merupakan blogging framework yang dibuat oleh [Brandon Mathis][] untuk [Jekyll][], merupakan engine blog yang membuat halaman html statis. Dibandingkan dengan [Jekyll][] kita harus membuat	template HTML, CSS, Javascript dan setting konfigurasi, dengan [Octopress][] yang perlu kita lakukan hanya meng-clone atau fork [Octopress][] dari [Github][] dan menginstall dependensi serta theme's, dan kita sudah siap menulis blog.
<!--more-->

1. Pastikan sudah menginstall [Git][] dan [Ruby 1.9.3][]
2. Clone atau fork [Octopress][]
		git clone git://github.com/imathis/octopress.git octopress
		cd octopress
3. Install dependensi
		gem install bundler
		bundle install
4. Install theme default Octopress
		rake install
5. Untuk menjalankannya di localhost
		rake generate
		rake preview
6. Arahkan browser ke alamat <http://localhost:4000>, akan tampak tampilan default Octopress
7. Untuk mencari theme lain bisa menuju ke <https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes>, untuk mengedit theme yang ada sesuai keinginan bisa mengikuti panduan ini <http://octopress.org/docs/theme/>
8. Panduan mengenai [Sass][] dan [Markdown][] juga tersedia bagi anda yang masih awam.
9. Untuk membuat post baru
		rake new_post["Judul Post"]
10. Secara default sudah banyak plugin yang terinstall di Octopress silahkan pelajari dokumentasinya untuk lebih jelas, dan juga banyak third party plugin, salah satu yang sempat saya gunakan kemarin adalah plugin [Table of Contents][].
11. Untuk deployment ada beberapa [pilihan][]. Akhirnya saya memilih deployment menggunakan [Heroku][].
12. Untuk deployment di Heroku, pertama-tama harus memastikan sudah menginstall gem heroku.
		gem install heroku
13. Selanjutnya buat heroku app untuk deployment, bisa melalui interface web Heroku ataupun dari command line, pastikan juga anda sudah punya akun di Heroku.
		heroku create
		git config branch.master.remote heroku
14. Edit .gitignore dalam root repositori anda, hilangkan pilihan public, agar konten kita bisa di upload ke Heroku
15. Dan akhirnya tambahkan blog anda ke Heroku, langkah ini juga dilakukan setiap saat anda mengupdate blog anda.
		rake generate
		git add .
		git commit -m 'site updated'
		git push heroku master
		
Selamat mencoba !!!

[Octopress]: http://www.octopress.org
[Brandon Mathis]: http://brandonmathis.com/
[Jekyll]: http://github.com/mojombo/jekyll
[Github]: https://github.com/imathis/octopress
[Git]: http://git-scm.com/
[Ruby 1.9.3]: http://octopress.org/docs/setup/rvm
[Sass]: http://sass-lang.com/tutorial.html
[Markdown]: http://daringfireball.net/projects/markdown/syntax
[Table of Contents]: http://brizzled.clapper.org/blog/2012/02/04/generating-a-table-of-contents-in-octopress/
[Pilihan]: http://octopress.org/docs/deploying/
[Heroku]: http://octopress.org/docs/deploying/heroku
