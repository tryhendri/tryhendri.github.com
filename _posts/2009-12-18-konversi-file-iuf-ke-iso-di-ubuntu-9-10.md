---
layout: post
title: Konversi File iuf ke iso di Ubuntu 9.10
date: 2009-12-18 15:06:05.000000000 +07:00
type: post
published: true
status: publish
categories:
- Ubuntu
tags:
- iso
- ubuntu 9.10
- uif
google_analytics : true
comments  : true
---
Ketika mendapatkan sebuah file hasil download dari internet, sempat bingung juga mendapatkan file berektensi *.iuf, bagaimana membukanya dengan software apa membuka file tersebut. *. uif (universal format image) adalah bentuk file format image terkompresi dalam CD/DVD.  karena di komputer ubuntu 9.10 yang di pakai ada aplikasi untuk membuka file *.iso, akhirnya diputuskanlah untuk mengubah dari file *.iuf ke *.iso.

setelah mencari-cari jawabanya akhirnya dapat tutorialnya, berikut saya tuliskan kembali tutorialnya :
- Install beberapa *tools* yang dibutuhkan untuk menginstall software konversi dari *.uif  ke *.iso dengan perintah :

{% highlight bash %}
sudo apt-get install zlib1g zlib1g-dev libssl-dev build-essential
{% endhighlight %}

- kemudian download aplikasi tersebut
{% highlight bash %}
wget http://aluigi.altervista.org/mytoolz/uif2iso.zip
{% endhighlight %}

- unzip file tersebut dengan perintah
{% highlight bash %}
unzip uif2iso.zip
{% endhighlight %}

- masuklah ke folder hasil ekstraksi tersebut
{% highlight bash %}
cd src
{% endhighlight %}

- buatlah executable dari apliaksi tersebut
{% highlight bash %}
make
sudo make install
{% endhighlight %}

- software uif2iso telah terinstall di ubuntu anda, selanjtunya tinggal menjalankanny, output file dari *.iso boleh ditulis apasaja asalkan tetap berkahiran *.iso

{% highlight bash %}
uif2iso example.uif output.iso
{% endhighlight %}

sekedar menuliskan saja maaf jika terlalau sederhana ilmunya...
