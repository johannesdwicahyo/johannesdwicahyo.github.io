---
title: "Hapus File Temporary di Ubuntu"
date: 2013-04-30 10:50
categories: Ubuntu, Temporary, Bash
---

Hari ini saat akan membuat tulisan baru, seperti biasa saya menggunakan [Sublime Text][1] sebagai editor favorit saya saat ini. Tapi ada satu tampilan yang mengganggu, list file saya bertambah panjang dua kali lipat karena adanya file temporary. File dengan akhiran "~" ini dalam keadaan biasa tidak mengganggu dan ukurannya sebenarnya juga tidak seberapa, tapi hari ini saya terganggu dan memutuskan mencari cara bagaimana untuk menghilangkannya.
<!--more-->
Setelah googling singkat untuk mencari cara, kebanyakan menunjukkan car menggunakan berbagai aplikasi pembersih seperti [BleachBit][2] yang baru saya bahas juga. Tapi tujuan saya bukan aplikasi seperti itu, saya lebih butuh script bash sederhana untuk menghilangkan file temporary dalam folder tertentu saja misalnya.

Akhirnya saya tertuju pada sebuah pertanyaan di [AskUbuntu][3], yang memiliki tujuan sama dengan saya, tetapi dia sudah sedikit lebih maju karena sudah berusaha membuat penyelesaian dengan menggunakan Bash Aliases. Dia berusaha membuat perintah tambahan untuk rm dengan mengedit file *~/.bash_aliases*.
``` bash
# aliases

# finds temporary files ending with '~' and deletes them
alias rm~='find . -name '*~' -print0 | xargs -0 /bin/rm -f'
```
Tapi perintah ini tampaknya tidak berjalan sehingga akhirnya dia bertanya dia bertanya di [AskUbuntu][3]. Dan tentu saja kemudian muncul member yang baik hati untuk menjawab, menjelaskan dan bukan hanya memberi solusi tapi juga memberikan masukan dan perbaikan.

Menurut saran dari user tersebut, script itu perlu diubah menjadi
``` bash
alias rm~='find . -name "*~" -type f -exec /bin/rm -fv -- {} +'
```

Dan dengan lebih baik lagi, dia memberikan saran untuk mengubahnya menjadi function. Kode lengkapnya seperti di bawah ini dengan tambahan argumen *--dry-run* untuk menampilkan list file temporary yang ada di folder tersebut.

``` bash
#removing temporary file, file ended with ~ sign
#script from http://askubuntu.com/questions/233544/command-for-deleting-temporary-files-ending-with
rm~() {
	case "$1" in
	"--dry-run")
		find . -name "*~" -type f -printf "Removing file %p\n"
		;;
	"")
		find . -name "*~" -type f -printf "Removing file %p\n" -delete
		;;
	*)
		echo "Unsupported option \`$1' . Did you mean --dry-run?"
		;;
	esac
}
```

Sudah saya coba dan berjalan dengan baik. Masalah saya selesai dengan cara yang elegan hari ini.

[1]: http://www.sublime-text.com
[2]: /blog/2013/04/30/bleachbit-ccleanernya-ubuntu/
[3]: http://askubuntu.com/questions/233544/command-for-deleting-temporary-files-ending-with