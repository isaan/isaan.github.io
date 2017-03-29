---
layout: post
title: "Install Ruby on Rails dengan RVM di Ubuntu 16.04"
date: 2016-12-21 09:42:28 +0700
comments: true
categories: [ruby on rails, ubuntu]
description: Langkah langkah menginstall Ruby on Rails dengan RVM di sistem operasi Ubuntu 16.04
keywords: ruby on rails, install ruby di ubuntu, install ubuntu dengan rvm.
---

{%img /images/2016/12/21/rubyonrails.jpg ruby on rails %}

**Ruby on Rails** adalah application stacks yang cukup populer di kalangan developer untuk membuat situs dan web apps. Ruby adalah bahasa pemrograman yang dikombinasikan dengan Rails framework, yang membuat development aplikasi menjadi sederhana.

<!-- more -->

**Menginstall Ruby on Rails** bisa dilakukan dengan dua cara yaitu dengan RVM dan RBENV. Kali ini saya akan bahas cara instalasi ruby on rails dengan RVM (Ruby Version Manager). Mengapa RVM? Karena dengan RVM memungkinkan Anda untuk manage dan bekerja dengan multiple Ruby environments dengan melakukan switch versinya.

Untuk *menginstall Ruby on Rails* dengan menggunakan RVM, Anda harus login dengan user biasa atau non-root user. Pertama kita gunakan "gpg command" untuk request public key dari RVM projects key.


**Instalasi**

{% codeblock %}
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
{% endcodeblock %}

Pindah ke directory yang writable locations seperti /tmp dan download RVM script. Gunakan curl untuk mendownload RVM instalasi script nya.

{% codeblock /tmp %}
$ \curl -sSL https://get.rvm.io -o rvm.sh
{% endcodeblock %}

Setelah selesai download, jalankan script *rvm.sh* nya

{% codeblock /tmp %}
$ less /tmp/rvm.sh
{% endcodeblock %}

Selama proses instalasi, akan muncul popup yang meminta untuk memasukkan password anda. Dan setelah selesai kanu bisa cek nya dengan mengetik 'rvm'

{% codeblock %}
$ rvm
{% endcodeblock %}


**Install Spesifik Ruby on Rails Version**

Jika anda ingin menginstall Ruby dengan versi tertentu, maka anda bisa mengetik command dibawah ini untuk menampilkan versi Ruby yang tersedia.

{% codeblock %}
$ rvm list known
{% endcodeblock %}

Dan setelah tampil daftar Ruby beserta versinya, ketika akan install dengan versi tertentu yaitu dengan cara:

{% codeblock %}
$ rvm install ruby_version
{% endcodeblock %}

Untuk "ruby_version" kamu bisa menulisnya dengan ruby-2.3.0 atau hanya 2.3.0. Setelah selesai, anda bisa cek versi Ruby yang telah diinstall dengan mengetik:

{% codeblock %}
$ rvm list
{% endcodeblock %}

Lalu ketika anda ingin switch atau ganti versi Ruby cukup mengetik:

{% codeblock %}
$ rvm use ruby_version
{% endcodeblock %}

Dan sejak rails adalah gem, kita bisa install beberapa jenis versi dari Rails dengan menggunakan "gem command".

{% codeblock %}
$ gem search '^rails$' --all
{% endcodeblock %}

Note: Untuk install rails anda hanya perlu menulis versi rails nya saja. Contoh: 4.2.0

{% codeblock %}
$ gem install rails -v rails_version
{% endcodeblock %}


**Install JavaScript Runtime**

Di beberapa fitur dari Rails, seperti Pipeline asset tergantung pada JavaScript Runtime. Maka dari itu kita akan menginstall node.js dengan mengguanakan command "apt-get".

{% codeblock %}
$ sudo apt-get update
$ sudo apt-get install -y nodejs
{% endcodeblock %}

Sampai langkah ini, anda bisa memulai untuk melakukan tes develop aplikasi web dengan menggunakan Ruby on Rails yang telah di install.