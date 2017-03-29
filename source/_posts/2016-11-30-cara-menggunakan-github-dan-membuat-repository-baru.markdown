---
layout: post
title: "Cara Menggunakan Github dan Membuat Repository Baru"
date: 2016-11-30 09:44:45 +0700
comments: true
categories: [github]
description:  Menggunakan github repository untuk developing program.
keywords: git, github, repository, programming, code.
---

{%img /images/2016/11/30/githome.jpg github repository %}

Setelah melakukan [install git](https://ikhsanir.com/blog/2016/11/29/cara-install-git-di-ubuntu-16-dot-04/), langkah selanjutnya adalah memulai untuk **menggunakan Github dan membuat repository baru** untuk aplikasi yang kita buat agar tersimpan dalam sistem versi kontrol dari *Github*.

<!-- more -->

Pertama login di situs Github dengan username dan password anda, kemudian klik **Create New Repository**.

{%img /images/2016/11/30/newrepo.png github repository %}

Isi nama repository dan deskripsinya. Di github ada dua jenis repository yaitu public dan private. Public artinya repository kita bisa diliat oleh semua orang sedangkan private itu nanti yg bisa liat cuma kita dan team yang kita tentukan saja, tetapi untuk private ini kita dikenakan biaya langganan $7/month. Untuk awal kita buat public terlebih dahulu untuk perkenalan dengan teknologinya, baru nanti kalau sudah mulai faham anda bisa *upgrade plan* ke paket private sendiri. Setelah itu klik **Create Repository**

{%img /images/2016/11/30/repo.gif github repository %}

Akan muncul tampilan "Quick setup" seperti gambar diatas. Ada dua opsi untuk melakukan setup yaitu dengan HTTPS atau SSH. Pilih salah satu dan kemudian masuk buka terminal dari desktop Ubuntu anda. Masuk ke directory kerja anda (dimana saja terserah) untuk melakukan clone repository yang telah anda buat di Github. Contoh disini saya mengguakan SSH untuk melakukan clone:

{% codeblock git clone %}
$ git clone git@github.com:isaan/timetracker.git
{% endcodeblock %}

{%img /images/2016/11/30/gitclone.png git clone %}

Lalu masuk ke directory yang telah di clone dari Github tersebut. Buat file apa saja untuk tes apakah repository sudah berfungsi.

{% codeblock git clone %}
$ echo "this is readme" >> README.md
{% endcodeblock %}

Diatas saya membuat file README.md yang isinya adalah this is readme. Lalu tambahkan ke git, commit, dan push ke server git.

{% codeblock git add %}
$ git add README.md
{% endcodeblock %}

{% codeblock git commit %}
$ git commit -m "add README"
{% endcodeblock %}

{% codeblock git push %}
$ git push -u origin master
{% endcodeblock %}

{%img /images/2016/11/30/gitadd.png git add %}

Jika tidak ada error dan muncul notifikasi seperti diatas, harusnya file *README.md* yang baru saja dibuat akan terkirim ke server github. Sekarang cek ke repository github Anda, file tersebut sudah masuk ke repository. Artinya repositroy tersebut sudah siap digunakan untuk dilakukan development.

{%img /images/2016/11/30/repository.png repository %}

Selanjutnya kita akan mencoba menambah directory di repository yang telah kita clone dan melakukan push ke github lagi.

{% codeblock git add %}
$ mkdir apps
{% endcodeblock %}

{% codeblock git commit %}
$ git commit -m "add directory"
{% endcodeblock %}

{% codeblock git push %}
$ git push -u origin master
{% endcodeblock %}

{%img /images/2016/11/30/gitadddir.png add directory %}

Ketika anda mengikuti mengikuti 3 cara diatas pasti directory yang dibuat tidak terkirim ke repository github. Walaupun 100 kali reload github tetap tidak ada directory yang baru saja dibuat ada disana. Mengapa? Karena directory yang dibuat tadi belum ada isinya alias kosong. 

Github tidak bisa menambah directory yang didalamnya tidak ada isinya, atau dengan kata lain git membacanya sebagai null. Jadi ketika anda melakukan commit dan push pasti git akan mengeluarkan notifikasi kalau branch repository nya up-to-date.

Cara agar directory tersebut masuk ke repository di github adalah dengan mengisinya file. Sebagai contoh saya menambah file index.php didalam directory apps yang tadi dibuat.

{% codeblock git add %}
$ touch apps/index.php
{% endcodeblock %}

Jangan lupa melakukan git add

{% codeblock git add %}
$ git add apps
{% endcodeblock %}

{% codeblock git commit %}
$ git commit -m "add index.php & directory"
{% endcodeblock %}

{% codeblock git push %}
$ git push -u origin master
{% endcodeblock %}

Sekarang refresh repository Github anda, akan muncul directory beserta isi file didalamnya.

{%img /images/2016/11/30/directory.png add directory %}

Sekian tutorial *menggunakan github dan membuat repository baru* kali ini, semoga bermanfaat. Salam.

<!-- ```sh

$ cd apps
$ touch apps/index.html
$ git add apps

``` -->