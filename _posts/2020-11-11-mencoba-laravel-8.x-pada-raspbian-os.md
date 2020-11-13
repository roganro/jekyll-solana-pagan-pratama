---
title: Mencoba Laravel 8.x pada Raspbian OS
author: Pagan
date: 2020-11-11T12:11:00+07:00
layout: post
teaser: Persiapan untuk membuat lingkungan pengembangan web menggunakan framework Laravel.
category: teknologi
tags:
- linux
- raspberry
- config
- instalasi
- framework
---

## Instalasi

### Perangkat lunak yang diperlukan 

Terdapat beberapa persyaratan yang mesti dipenuhi untuk menginstal laravel di sebuah mesin, silahkan pasang terlebih dahulu beberapa aplikasi berikut:

- PHP >= 7.3
- BCMath PHP Extension
- Ctype PHP Extension
- Fileinfo PHP Extension
- JSON PHP Extension
- Mbstring PHP Extension
- OpenSSL PHP Extension
- PDO PHP Extension
- Tokenizer PHP Extension
- XML PHP Extension

Bagi yang memakai raspbian 32-bit, silahkan install paket berikut dari repo raspbian:

```sh
sudo apt install php php7.3 php-bcmath php7.3-bcmath php-common php7.3-common php-json php7.3-json php-mbstring php7.3-mbstring openssl php7.3-xml php7.3-xmlrpc -y
```

Jangan lupa untuk memeriksa versi php:

`php -v`

Jika hasilnya seperti gambar dibawah ini, berarti php sudah berjalan

![php_version](/i/php_version.png){:class="image-wrapper-left__list"}

### Memasang Composer serta mengatur PATH untuk BASH

Sebelum menginstall laravel, kita harus memasang composer terlebih dahulu sebagai manajer paket bagi php:

```sh
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'c31c1e292ad7be5f49291169c0ac8f683499edddcfd4e42232982d0fd193004208a58ff6f353fde0012d35fdd72bc394') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
mv composer ~/.local/bin
```

Sekarang atur *PATH-nya* agar bisa digunakan dimana saja:

```sh
echo '# PATH Composer dan Laravel' >> .bashrc
echo 'export COMPOSER_LARAVEL="$HOME/.local"' >> .bashrc
echo 'export PATH="$HOME/.local/bin:$PATH"' >> .bashrc
```

Seperti sebelumnya, sekarang cek versi composernya dari *directory* manapun:

`composer --version`

Hasilnya akan seperti gambar dibawah

![composer_version](/i/composer_version.png){:class="image-wrapper-left__list"}

### Memasang Laravel menggunakan Composer

Pertama, unduh terlebih dahulu **Laravel Installer** menggunakan composer:

`composer global require laravel/installer`

Buka kembali **BASH Shell** untuk mengatur *PATH* laravel:

```sh
sed -i 's+export COMPOSER_LARAVEL="$HOME/.local"+export COMPOSER_LARAVEL="$HOME/.local:$HOME/.config/composer/vendor"+g' .bashrc
sed -i 's+export PATH="$HOME/.local/bin:$PATH"+export PATH="$HOME/.local/bin:$HOME/.config/composer/vendor/bin:$PATH"+g' .bashrc
```

Sebelum memulai untuk memasang laravel, kita cek terlebih dulu versi laravel *installer-nya*, sekalian memastikan apakah sudah berjalan atau tidaknya:

`laravel --version`

kalau sudah berjalan dengan baik, akan seperti ini:

![Laravel_Installer_Version](/i/laravel_installer_version.png){:class="image-wrapper-left__list"}

Selanjutnya tinggal membuat sebuah *project* web menggunakan laravel installer:

`laravel new website`

kita cek versi laravel yang terpasang:

```sh
cd website
php artisan --version
```

![Laravel_Version](/i/laravel_version.png){:class="image-wrapper-left__list"}