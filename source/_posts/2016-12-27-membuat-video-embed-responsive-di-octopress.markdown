---
layout: post
title: "Membuat Video Embed Responsive di Octopress"
date: 2016-12-27 17:04:25 +0700
comments: true
categories: [octopress, ruby on rails, plugin]
description: Cara embed video responsive dari youtube, vimeo, dan dailymotion di Octopress. 
keywords: embed video octopress, embed video responsive octopress, embed video vimeo octopress.
---

{% img /images/2016/12/27/octocode.jpg %}

Dalam framework Octopress, untuk melakukan penulisan artikel beda dengan framework blogging yang lain. Di Octopress menggunakan syntax markdown. Jadi ketika kita ingin memasukkan misalkan gambar maka menggunakan syntax "img (lokasi gambar)".

<!-- more -->

Yang jadi pertanyaan adalah **bagaimana melakukan embed video dari Youtube** atau beberapa situs video yang lain? Jika dalam framework blogging lain untuk melakukan embed adalah dengan langsung memasukkan *embed code* dari Youtube.

Sebenarnya di Octopress ketika menulis artikel dan ingin menyisipkan atau embed video bisa langsung ditulis atau paste embed code yang kita dapatkan dari video youtube tersebut, tetapi setelah saya tes ternyata hasilnya belum responsive, dimana tampilan video nya akan berantakan ketika dibuka pada tampilan mobile. 

Berikut adalah beberapa code untuk mengakalinya agar video yang kita embed menjadi responsive. Tambahkan file atau buat file baru di dalam directory ".../plugins" anda dan isi dengan ruby code dibawah ini.

**1. Code Embed Youtube**

{% codeblock youtube.rb https://github.com/optikfluffel/octopress-responsive-video-embed/blob/master/youtube.rb %}
module Jekyll
  class Youtube < Liquid::Tag

    def initialize(name, id, tokens)
      super
      @id = id
    end

    def render(context)
      %(<div class="embed-video-container"><iframe src="//www.youtube.com/embed/#{@id.strip}" allowfullscreen></iframe></div>)
    end
  end
end

Liquid::Template.register_tag('youtube', Jekyll::Youtube)
{% endcodeblock %}

**2. Code Embed Vimeo**

{% codeblock vimeo.rb https://github.com/optikfluffel/octopress-responsive-video-embed/blob/master/vimeo.rb %}
module Jekyll
  class Vimeo < Liquid::Tag

    def initialize(name, id, tokens)
      super
      @id = id
    end

    def render(context)
      %(<div class="embed-video-container"><iframe src="//player.vimeo.com/video/#{@id.strip}"></iframe></div>)
    end
  end
end

Liquid::Template.register_tag('vimeo', Jekyll::Vimeo)
{% endcodeblock %}

**3. Code Embed Dailymotion**

{% codeblock dailymotion.rb https://github.com/optikfluffel/octopress-responsive-video-embed/blob/master/dailymotion.rb %}
module Jekyll
  class DailyMotion < Liquid::Tag
    def initialize(name, id, tokens)
      super
      @id = id
    end
    def render(context)
	%(<div class="embed-video-container"><iframe src="//www.dailymotion.com/embed/video/#{@id.strip}"></iframe></div>)
    end
  end
end
Liquid::Template.register_tag('dailymotion', Jekyll::DailyMotion)
{% endcodeblock %}

Setelah anda menambahkan file tersebut didalam *plugins* selanjutnya adalah menambahkan file .scss didalam folder sass Anda. Jika Anda menggunakan theme custom (bukan theme bawaan dari Octopress) maka lokasinya adalah disini "../sass/(nama theme)/custom/". Namun bila anda menggunakan theme lain atau default Anda bisa menyesuaikannya lokasinya. Tambahkan file "_rve.scss" dibawah ini didalam directory tersebut.

{% codeblock _rve.scss https://github.com/optikfluffel/octopress-responsive-video-embed/blob/master/_rve.scss %}
.embed-video-container {
  position: relative;
  padding-bottom: 56.25%; /* 16/9 ratio */
  padding-top: 30px; /* IE6 workaround*/
  height: 0;
  overflow: hidden;
  margin-bottom: 1.5em;

  iframe, object, embed {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
}
{% endcodeblock %}

Sampai sejauh ini cara diatas sudah selesai dan siap untuk dilakukan testing. Untuk post video atau embed video di dalam post artikel caranya adalah:

**1. Vimeo**

Syntax penulisan embed vimeo.

{% img /images/2016/12/27/vimeo.png %}

Contoh Vimeo Embed:
{% vimeo 188608314 %}

**2. Youtube**

Syntax penulisan embed youtube.

{% img /images/2016/12/27/youtube.png %}

Contoh Youtube Embed:
{% youtube N-GNV7jhKV4 %}

**3. Dailymotion**

Syntax penulisan embed dailymotion.

{% img /images/2016/12/27/dailymotion.png %}

Contoh Dailymotion Embed:
{% dailymotion x56eaeo %}

Diatas ada beberapa contoh embed dari Vimeo, Youtube, dan Dailymotion. Jika anda mengikuti proses dari awal harusnya sudah berhasil embed video nya dan akan responsive ketika dibuka di mobile. 

Sekian *cara embed video responsive di Octopress*. Semoga membantu. Code credit ada [disini](https://github.com/optikfluffel/octopress-responsive-video-embed).