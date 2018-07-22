---
layout: post
title: "Memasang Google Tag Manager di Octopress"
date: 2018-07-22 12:51:12 +0700
comments: true
categories: [octopress, google tag manager, analytics]
description: Google Tag Manager adalah sistem pengelolaan tag yang memungkinkan kamu dengan cepat dan mudah mengupdate tag dan script code di situs atau aplikasi mobile.
keywords: memasang google tag manager di octopress, cara pasang gtm di octopress, cara memasang google tag manager octopress, google tag manager octopress
---

{% img /images/2018/07/22/Google-Analytics-Tag-Manager.png %}

Di artikel kali ini saya akan membahas mengenai **Cara Memasang Google Tag Manager di Octopress**. Apa itu Google Tag Manager atau yang biasa dikenal GTM? Bagi yang belum tahu Google Tag Manager adalah sistem pengelolaan tag yang memungkinkan kamu dengan cepat dan mudah mengupdate tag dan script code di situs atau aplikasi mobile. <!-- more -->

Setelah script code dari Tag Manager ditambahkan ke website atau aplikasi, kamu dapat mengonfigurasi tag melalui interface pengguna berbasis web tanpa harus mengubah dan menerapkan kode tambahan. Hal ini mengurangi error dan membebaskan kamu dari keharusan untuk melibatkan developer kapan saja jika perlu melakukan perubahan.

Google Tag Manager juga merupakan salah satu fitur dari Google Analytics (GA) yang digunakan untuk membantu marketing dalam manajemen tag yang dibutuhkan untuk analisa kebiasaan pengguna dalam suatu website atau aplikasi. Melalui Google Tag Manager ini kamu bisa mendeteksi kebiasaan user misalnya adalah mendeteksi user yang membuka halaman detail artikel / produk, dimana nantinya data tersebut akan dikirim ke Google Analytics untuk memantau kebasaan pengguna.

*Memasang Google Tag Manager di Octopress* ini bisa dibilang sangat mudah, karena kita hanya perlu memasang script js yang telah disediakan ke dalam tag head dan body di dalamnya. Namun di dalam octopress ini terdapat banyak sekali file yang berisi tag head dan body di dalamnya, sehingga ketika saya mau implementasi nya sedikit bingung mau di pasang di file yang mana. Saya sudah googling beberapa kali dan tidak ada artikel yang menjelaskan cara pasang gtm di octopress, akhirnya saya coba untuk riset sendiri karena memang perlu ekstra tenaga untuk memasangnya. Haha, bercanda. :)

Ok berikut adalah langkah langkahnya :

Masukkan nama akun beserta alamat website yang ingin dipasang GTM. Nama akun digunakan sebagai ID jika kamu memiliki beberapa website yang ingin di analisa.

{% img /images/2018/07/22/1.png %}

Lalu untuk alamat website ini nanti akan digunakan sebagai preview, untuk mengetahui apakah tag tersebut sudah berjalan atau belum.

{% img /images/2018/07/22/2.png %}

Setelah itu kamu akan disuguhkan dengan popup yang berisi script js yang harus dipasang di website.

{% img /images/2018/07/22/3.png %}

Terdapat dua script yang harus kamu pasang pada bagian head dan body di semua halaman website kamu. Di Octopress terdapat banyak sekali file yang di dalamnya terdapat tag head dan body. Untuk itu kamu harus menemukan root / inti dari file yang digunakan di semua halaman. Untuk website saya menggunakan theme Oscalite, jadi saya memasangnya di bagian ini :

**Script Head**
{% codeblock %}
(repo)/source/_includes/site/head.html
{% endcodeblock %}

**Script Body**
{% codeblock %}
(repo)/source/_layouts/default.html
{% endcodeblock %}

*Note: struktur file diatas mungkin bisa beda dengan yang kamu miliki, namun tetap bisa disesuaikan di inti file yang digunakan, biasanya default nya di dalam directory /source/_layouts*

Jangan lupa simpan lalu generate dan preview dulu di local.

{% codeblock %}
bundle exec rake generate
bundle exec rake preview
{% endcodeblock %}

Buka local development kamu di localhost:4000, dan jika sudah berhasil maka akan muncul preview dari Google Tag Manager.

{% img /images/2018/07/22/4.png %}

Jika belum muncul preview dari Google Tag Manager kamu bisa mengeceknya melalui view source di home page nya dengan cara
*view-source:localhost:4000*. Disana akan kelihatan apakah script tersebut sudah berhasil terpasang atau belum.

Setelah sukses muncul di local artinya script sudah terpasang dengan benar, maka kamu bisa melakukan deploy agar bisa tampil di live nya.

{% img /images/2018/07/22/5.png %}

Sekian tutorial dari saya mengenai <span style="text-decoration:underline">cara memasang google tag manager di octopress</span>. Untuk bagaimana menggunakan tag nya akan saya bahas di artikel selanjutnya. Semoga bermanfaat :)