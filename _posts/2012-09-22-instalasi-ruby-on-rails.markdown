---
title: "Instalasi Ruby on Rails"
date: 2012-09-22 08:05
categories: [ruby, rails, rvm, install, ubuntu]
---

Rails bisa di-install di berbagai macam platform. Baik Linux, Windows maupun Macintosh. Macintosh merupakan OS favorit untuk Rails developer, didukung juga karena adanya TextMate, yang dianggap text editor paling powerfull. Saya sendiri belum pernah mencoba develop aplikasi Rails di Mac, karena tidak mempunyainya, karena itu untuk petunjuk instalasi Mac, saya juga tidak bisa berikan. Kalau saya perkirakan seharusnya mirip dengan di Linux, karena sama-sama berbasis UNIX.
<!--more-->
Sementara untuk instalasi di Windows bisa dengan relatif mudah dan ringkas dilakukan dengan RailsInstaller. Saya rasa langkah-langkahnya cukup mudah, cukup menuju ke website tadi dan saya yakin anda akan berhasil menginstall Rails di Windows.

Untuk OS Linux, Rails juga sebenarnya mudah diinstall. Saya contohkan misalnya dengan menggunakan OS Ubuntu. Ada panduan resmi dari Ubuntu Help, tetapi sepertinya sudah outdated ya, karena masih menggunakan Ubuntu 9.04. Instalasi Rails bisa menggunakan RVM dan bisa juga tidak, beberapa orang menganggap menggunakan RVM akan lebih baik, karena sistem Ruby yang didapatkan akan lebih update daripada package Ruby yang didapat dari apt-get.

Instalasi Tanpa RVM

Kita akan menginstall : Ruby 1.9.2, Rails 3.20, Rubygems 1.8.15, MySQL, SQLite dan GIT
* Update terlebih dulu sistem Ubuntu kita
		sudo apt-get update
* Install Ruby 1.9.2, build-essential dan GIT
		sudo apt-get install ruby1.9.2-full build-essential git-core
* Install and update Rubygems 1.8.15
		wget http://production.cf.rubygems.org/rubygems/rubygems-1.8.15.tgz
		tar -zxvf rubygems-1.8.15.tgz
		cd rubygems-1.8.15
		sudo ruby setup.rb
		sudo gem update --system
		sudo gem install rubygems-update
		sudo update_rubygems
* Install Rails, MySQL dan SQLite
		sudo gem install rails
		sudo apt-get install libsqlite3-dev
		sudo gem install sqlite3
		sudo apt-get install nodejs
		sudo apt-get install mysql-server mysql-client
		sudo apt-get install libmysql-ruby libmysqlclient-dev
		sudo gem install mysql
* Cek Instalasi 
		#Untuk mengecek apakah instalasi sudah berhasil atau belum
		rails new my_app
		cd my_app
		bundle install
		rails generate model User
		#Seharusnya bila tidak ada error, berarti instalasi Rails sudah berhasil

Instalasi dengan RVM

* Install Git
		sudo apt-get install git
* Install Curl
		sudo apt-get install curl
* Install RVM
		bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)
		#Edit bashrc agar meload RVM di shell session
		gedit ~/.bashrc
		#Tambahkan kode berikut di baris akhir
		[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"
		# Load RVM into a shell session *as a function*
		#Reload shell dan cek instalasi RVM
		source ~/.bashrc
		type rvm | head -1
* Install RVM requirements
		#Cek RVM requirements
		rvm requirements
		#Install requirement
		sudo apt-get install build-essential openssl libreadline6 libreadline6-dev zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion
* Install Ruby
		#Install Ruby
		rvm install 1.9.2
		#Gunakan Ruby yang baru
		rvm use 1.9.2
		#Cek versi Ruby
		ruby -v
* Install Rails
		#Gem akan terinstal bersama RVM dan Ruby
		gem install rails
* Cek Instalasi
		#Cek instalasi dengan membuat aplikasi baru
		rails new my_app
		bundle install
		cd my_app
		rails server
		#Seharusnya aplikasi berjalan di http://localhost:3000
* Bila memilih menggunakan MySQL
		sudo apt-get install mysql-server
		gem install mysql2
		rails new [project name] -d mysql

Selamat mencoba semoga berhasil, dari saya memang lebih menyarankan instalasi menggunakan RVM.
