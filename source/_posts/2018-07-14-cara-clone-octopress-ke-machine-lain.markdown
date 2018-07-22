---
layout: post
title: "Cara Clone Octopress ke Machine Lain"
date: 2018-07-14 08:35:31 +0700
comments: true
categories: [octopress]
description: cara clone repository octopress ke komputer lain
keywords: clone octopress, cara clone octopress, cara termudah clone octopress
---

{% img /images/2018/07/14/gambar.png %}

**Clone Octopress** adalah melakukan copy data octopress yang berada di repository Github ke dalam machine lain. Clone Octopress ini dilakukan jika kita sebelumnya kita pernah install octopress dengan machine lain dan sekarang ingin melakukan clone ke laptop kita sendiri. <!-- more -->

Dalam artikel ini saya akan membahas bagaimana caranya melakukan clone octopress ke machine / komputer lain. Bagi kamu yang belum tahu apa itu octopress, bisa baca dulu disini [apa itu octopress?](http://octopress.org). 

Artikel ini saya buat sesuai dengan case saya saat ini yaitu ketika saya menggunakan octopress pertama kali saya menggunakan PC, sedangkan sekarang saya menggunakan laptop pribadi saya. Untung data nya tersimpan utuh di dalam Github sehingga kapanpun akan menggunakan kembali tinggal clone saja repository tersebut.

Sebelum melakukan *clone octopress* tentu saja kamu harus install git dan ruby terlebih dahulu. Kamu bisa menggunakan rvm atau rbenv untuk menginstall ruby. Kalau saya saat ini menggunakan rbenv dan menggunakan sistem operasi Mac OS.

Setelah semua prerequisites (persyaratan) yang dibutuhkan ter install. Selanjutnya kamu langsung bisa melakukan clone repository github kamu. Oiya  yang perlu diperhatikan disini adalah kamu harus melakukan clone repository octopress anda yang terdapat Gemfile nya. Dalam hal ini di repository saya terdapat 2 branch, master (sebagai production), dan source (sebagai development). Untuk itu saya melakukan clone ke dalam branch source saya. Mungkin masing masing repository akan ada perbedaan disini, disesuaikan aja sesuai kebutuhan. 

Format standar untuk melakukan clone adalah seperti ini :

{% codeblock %}
git clone (git repo kamu)

git clone -b (nama branch) (git repo kamu)
{% endcodeblock %}

Saya menggunakan format yang nomer dua karena saya perlu clone di branch tertentu.

{% codeblock %}
git clone -b source git@github.com:isaan/isaan.github.io.git
{% endcodeblock %}

Setelah selesai clone masuk ke directory tersebut dan clone branch master dan taruh di directory *_deploy*. Hal ini sangat diperlukan karena sewaktu deploy akan menggunakan directory *_deploy* ini. Jadi struktur directory nya nanti adalah :

{% codeblock %}
hasil clone dari branch source akan disimpan disini
/User/Projects/Directory_Clone_Source

hasil clone dari branch master akan berada di dalam directory hasil clone branch source
/User/Projects/Directory_Clone_Source/_deploy
{% endcodeblock %}

Berikut adalah command lebih lengkapnya

{% codeblock %}
cd /User/Projects/Directory_Clone_Source

git clone -b master git@github.com:isaan/isaan.github.io.git _deploy

cd _deploy

git status #untuk melihat status git terakhir, apakah uptodate atau ada yang masih conflict

git pull origin master #untuk pull data di repo agar sama dengan di lokal kita
{% endcodeblock %}

Tunggu beberapa saat hingga proses clone selesai. Setelah proses selesai masuk ke directory hasil clone tersebut dan pastikan ada Gemfile di dalamnya. Ketikkan command berikut ini di dalam directory tersebut, dalam case ini di root directory dari hasil clone source.

{% codeblock %}
gem install bundler

rbenv rehash (jika kamu menggunakan rbenv, perintah ini diperlukan untuk bisa menggunakan bundle command)

bundle install 

rake install (di versi ruby terbaru terkadang muncul error, kamu bisa menambah perintah "bundle exec rake install")

{% endcodeblock %}

{% img /images/2018/07/14/1.png %}

Jika kamu menggunakan custom theme sendiri alias bukan menggunakan theme default dari octopress biasanya akan muncul popup berikut ini.

{% img /images/2018/07/14/2.png %}

Kamu bisa melakukan pilihan disini, ketik ‘y’ untuk kembali menggunakan theme default octopress, atau ketik ’n’ untuk tetap menggunakan theme custom kamu.

Sampai proses ini seharusnya proses clone ke local machine kamu sudah selesai. Untuk melakukan testing apakah sudah berhasil atau belum, kamu bisa melakukan testing membuat post baru dengan perintah

{% codeblock %}
rake new_post[“(judul post)”]
{% endcodeblock %}

Jika error tambahkan perintah bundle exec di depannya

{% codeblock %}
bundle exec rake new_post[“(judul post)”]
{% endcodeblock %}

Atau bisa juga dengan perintah yang lebih simpel yaitu 

{% codeblock %}
rake new_post

Enter a title for your post: ...... #masukkan judul post nya
{% endcodeblock %}

Untuk melihat hasil post nya bisa di tes di local browser kamu terlebih dahulu.

{% codeblock %}
rake preview atau bundle exec rake preview
{% endcodeblock %}

Buka browser kamu dengan alamat berikut ini localhost:4000. Jika langkah langkah clone sudah benar harusnya sudah muncul hasilnya.

Ini adalah halaman home di local server development.
{% img /images/2018/07/14/3.png %}

Ini adalah detail page nya di local server development.
{% img /images/2018/07/14/3.png %}

Setelah semua oke, kamu bisa melakukan proses generate dan deploy ke live dengan perintah berikut ini.

{% codeblock %}
bundle exec rake generate

bundle exec rake deploy
{% endcodeblock %}

Jika sudah selesai maka hasilnya bisa dilihat di website anda. Di tempat saya hasilnya adalah seperti ini.

{% img /images/2018/07/14/5.png %}

{% img /images/2018/07/14/6.png %}

Hal yang perlu diketahui apakah proses deploy sudah selesai belum adalah kamu bisa mengecek status git nya di directory nya.

{% codeblock %}
cd /User/Projects/Directory_Clone_Source/_deploy

git status
{% endcodeblock %}

Jika yang muncul adalah *Your branch is up to date with 'origin/master'. Nothing to commit, working tree clean* maka directory tersebut adalah sudah clean dan sudah berhasil ke push ke github branch master. Kamu bisa mengeceknya di Github.

Lalu jika kamu cek status git di source maka akan muncul bahwa terdapat file yang di modifikasi dan belum ter push. Hal ini karena khusus di bagian source ini kamu harus push ke github secara manual

{% img /images/2018/07/14/7.png %}

Cara push ke github nya bisa dengan cara berikut ini.

{% codeblock %}
git add .
git commit -m 'update bla bla'
git push origin source
{% endcodeblock %}

*note: perintah di atas bisa di sesuaikan dengan kondisi kamu, misal nama branch nya*

Sekian adalah tutorial *Cara Clone Octopress ke Machine Lain*. Semoga bermanfaat. :)