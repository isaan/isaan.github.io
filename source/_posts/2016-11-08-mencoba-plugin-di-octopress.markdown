---
layout: post
title: "Mencoba Plugin di Octopress"
date: 2016-11-08 10:43:40 +0700
comments: true
categories: [octopress, plugin, ruby on rails]
description:  Menggunakan plugin di Octopress untuk memperindah tampilan dari post artikel.
keywords: octopress, framework, jekyll, programming.
---

{%img /images/2016/11/08/octopress.jpg octopress %}

Beberapa waktu yang lalu saya baru saja menginstall Octopress, yaitu blogging framework yang terkenal untuk hacker (katanya seperti itu :D). Oke langsung saja, jadi di Octopress ada beberapa plugin yang bisa digunakan untuk ditambahkan di post artikel. Berikut adalah beberapa pluginnya.

<!-- more -->

**1. Code Block**
Dengan plugin ini kamu bisa menulis blok kode secara langsung dalam posting Anda dan bisa juga dengan menambahkan judul dan link.

Contoh:
{% codeblock The code lang:ruby http://octopress.org/docs/plugins/codeblock/ %}
puts "Hello world!" Happy monday!
{% endcodeblock %}

**2. Image Tag** 
Plugin ini memungkinkan kamu untuk menambah gambar di dalam post artikel. Di octopress untuk menambah gambar menggunakan Markdown syntax. Memasukkan gambar di Octopress ada dua jenis yaitu memasukkan gambar dari website / link url gambar tersebut.

Contoh Gambar dari Link Web Lain:
{%img http://getpcsoft.wikisend.com/img_howto/0/322/yosemite.jpg Mac OS X Yosemite%}

Dan yang kedua adalah memasukkan gambar kita sendiri dari Local. Caranya yaitu dengan copy gambar yang akan di post misal dari hasil screenshot ke dalam folder '/source/images'. Setelah itu url pada gambar ubah menjadi /images/namagambar.png.

Contoh Gambar Local:
{%img /images/2016/11/08/screenshot.png Octopress %}

Bedanya adalah ketika memasukkan gambar dari link web lain otomatis itu bukan milik kita tetapi milik gambar orang tertentu, dan kita bisa terkena hak cipta jika suatu saat yang punya gambar menuntut. Sedangkan jika memasukkan gambar sendiri itu artinya gambar milik kita sendiri misal dari hasil Screenshot, foto objek tertentu, dll. Cara membedakan apakah gambar itu diambil dari link web lain atau upload sendiri adalah dengan klik kanan pada gambar dan open image in new tab.

**3. HTML5 Video Tag**
Plugin ini memungkinkan kamu untuk memasukan video mp4 yang di encode dalam format HTML 5 video di dalam post. 

{% video http://s3.imathis.com/video/zero-to-fancy-buttons.mp4 640 320 https://s17.postimg.org/ii43hq61r/fancy_button.png %}

**4. Include Code**
Untuk menampilkan isi code tertentu, arahkan path directory tersebut. Default dari Octopress adalah di dalam directory 'source/....' 
{% include_code javascripts/github.js %}

**5. Blockquote**
Blockquote plugin mengambil penulis, sumber, judul dan kutipan, dan juga HTML Semantik.
Contoh:
{% blockquote @allanbranch https://twitter.com/allanbranch/status/90766146063712256 %}
Over the past 24 hours I've been reflecting on my life & I've realized only one thing. I need a medieval battle axe.
{% endblockquote %}

<!-- **6. Puts** -->