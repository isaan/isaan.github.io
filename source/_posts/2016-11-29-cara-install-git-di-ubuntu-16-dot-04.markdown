---
layout: post
title: "Cara Install Git di Ubuntu 16.04"
date: 2016-11-29 16:03:14 +0700
comments: true
categories: [github]
description:  Menginstall git di linux Ubuntu 16.04.
keywords: git, github, repository, programming, code.
---

{%img /images/2016/11/29/gitlogo.jpg git %}

Dalam pengembangan software (perangkat lunak) modern sangat memerlukan alat sistem kontrol versi atau yang lebih dikenal dengan *version control*. Sistem kontrol versi memungkinkan Anda untuk melacak software atau aplikasi yang anda kerjakan pada tingkat sumber. Salah satu sistem kontrol versi yang paling populer di kalangan developer adalah Git, sistem kontrol versi terdistribusi. 

<!-- more -->

Adapun Git bisa mendukung sistem operasi yang banyak digunakan oleh user saat ini seperti Mac, Linux, dan Windows. Berikut adalah **tutorial install git** di Ubuntu 16.04 Desktop.

**1. Install Git dengan apt**

Ini adalah cara paling mudah karena anda dengan cepat memasang git dengan memanfaatkan repositori Ubuntu.

{% codeblock root@xboct:~$ %}
$ sudo apt-get update
$ sudo apt-get install git
{% endcodeblock %}


**2. Setup Git**

Setelah berhasil install git, selanjutnya adalah melakukan config git. Untuk config kali ini memerlukan username dan email yang anda daftarkan di Github. Jika anda belum memiliki akun *Github*, anda bisa mendaftarnya [disini](https://github.com/). 

Jika sudah memilik akun Github anda langsung menuju config dibawah ini"

{% codeblock root@xboct:~$ %}
$ git config --global user.name "Your Name" -> isi dengan username Github anda
$ git config --global user.email "youremail@domain.com" -> isi dengan email yg anda daftarkan di Github
{% endcodeblock %}

Setelah sudah anda bisa melihat konfigurasi tersebut dengan command dibawah ini

{% codeblock root@xboct:~$ %}
$ git config --list
{% endcodeblock %}

Maka akan tampil konfigurasi yang telah dilakukan

{% codeblock git configuration %}
user.name=your name
user.emai=youremail@domain.com
{% endcodeblock %}

Konfigurasi dari akun Github tersebut disimpan di ~/.gitconfig. Untuk melihatnya ketik command:

{% codeblock ~/.gitconfig %}
$ cat ~/.gitconfig
{% endcodeblock %}

{% codeblock ~/.gitconfig %}
[user]
	name = your name
	emai = youremail@domain.com
{% endcodeblock %}

Sekarang Ubuntu 16.04 Desktop anda sudah terinstall git dan sudah siap digunakan.