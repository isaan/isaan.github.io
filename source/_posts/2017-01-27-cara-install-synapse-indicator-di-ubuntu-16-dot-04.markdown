---
layout: post
title: "Cara Install Synapse Indicator di Ubuntu 16.04"
date: 2017-01-27 10:50:41 +0700
comments: true
categories: [ubuntu, linux]
description: Langkah install synapse indicator di top bar pada Ubuntu 16.04
keywords: install synapse ubuntu 16.04, cara install synapse di ubuntu, install synapse indicator
---

{% img /images/2017/01/27/synapseindicator.jpg %}

**Synapse Indicator** adalah aplikasi alternatif Spotlight yang dibuat oleh [Tom Beckmann](https://plus.google.com/+TomBeckmann/posts). Synapse Indicator sangat membantu kita dalam melakukan pencarian file, folder ataupun aplikasi. Dengan posisi search button diatas tentu mirip dengan spotlight di MacOS. <!-- more -->

Synapse Indicator sangat cepat dalam melakukan pencarian ketika Anda menggunakan themes custom MacOS seperti yang saya pakai ini. Kecuali anda masih menggunakan theme bawaan dari Ubuntu 16.04 Xenial Xerus, maka untuk melakukan pencarian tinggal mengetikan apa yang anda cari di sebelah kiri atas. Dibanding dengan fitur pencarian *Spotlight Apple*, keduanya merupakan perangkat pencarian berdasarkan menu yang menunjukkan top hit dari hasil file, aplikasi, dan sebagainya.

Dalam penulisan artikel ini saya menggunakan sistem operasi Ubuntu 16.04. Berikut adalah **langkah yang perlu anda lakukan ketika ingin memasang Synapse Indicator di Ubuntu Desktop 16.04**.

Tambahkan repository berikut ini sebelum install Synapse.

{% codeblock %}
sudo add-apt-repository ppa:noobslab/apps
sudo apt-get update
sudo apt-get install indicator-synapse
{% endcodeblock %}

Jika sewaktu melakukan install Synapse Indicator anda menemui error itu karena maka solusinya adalah dengan mengganti distribution pada repository yang baru saja anda tambahkan dari Xenial menjadi Trusty. Maksud dari mengganti repo distribution tersebut adalah agar kita bisa install aplikasi di Ubuntu 16.04 dengan repo dari Ubuntu 14.04 Trusty Tahr.

Cara mengganti repository distributionnya adalah dengan langkah berikut:
**System Settings > Software & Updates > Other Software > Cari apps repository dari noobslab dan klik Edit > Change Distribution Value menjadi "trusty"**

{% img /images/2017/01/27/systemsetting.png %}

{% img /images/2017/01/27/othersoft.png %}

{% img /images/2017/01/27/editsource.png %}

Setelah itu update dengan "sudo apt-get update" dan install synapse nya "sudo apt-get install indicator-synapse".

Thats it! Restart Komputer Anda, akan anda temui "search button" di top bar Ubuntu 16.04 anda yang bisa membantu bekerja lebih cepat dalam menemukan file ataupun aplikasi.

Sekian *Cara Install Synapse Indicator di Ubuntu 16.04*. Semoga bermanfaat.