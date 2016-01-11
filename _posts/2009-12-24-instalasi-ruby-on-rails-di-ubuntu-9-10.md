---
layout: post
title: Instalasi Ruby On Rails Di Ubuntu 9.10
date: 2009-12-24 14:25:42.000000000 +07:00
type: post
published: true
status: publish
categories:
- Perenungan
- Rails
tags:
- mysql
- Rails
- Ruby
- ubuntu 9.10
google_analytics : true
comments  : true
---
Ketika bermigrasi ke Ubuntu 9.10 Koala Karmic, saya coba untuk melakukan instalasi ulang Ruby dan Rails-nya, berikut adalah tahapan yang saya lakukan, semua tahapan dibawah ini diasumsikan terkoneksi dengan internet

**Pertama** : memastikan beberapa software yang dibutuhkan selama proses instalasi telah terinstal,
{% highlight bash %}
  sudo apt-get install build-essential
{% endhighlight %}

**Kedua** : proses selanjutnya adalah menginstall Ruby dan paket database MYSQL, jika anda memilih untuk menggunakan sqlite, instalasi MYSQL tidak dibutuhkan karena sqlite merupakan paket bawaan dari Rails-nya,
{% highlight bash %}
  sudo apt-get install ruby ri rdoc mysql-server libmysql-ruby ruby1.8-dev irb1.8 libdbd-mysql-perl libdbi-perl libmysql-ruby1.8 libmysqlclient15off libnet-daemon-perl libplrpc-perl libreadline-ruby1.8 libruby1.8 mysql-client-5.1 mysql-common mysql-server-5.1 rdoc1.8 ri1.8 ruby1.8 irb libopenssl-ruby libopenssl-ruby1.8 libhtml-template-perl mysql-server-core-5.1 libmysqlclient16 libreadline5 psmisc
{% endhighlight %}

saat proses instalasi anda akan diminta untuk memasukan root *password*

**Ketiga** : install paket Ruby Gems dari [rubyforge.org](http://www.rubyforge.org), versi yang digunakan disini adalah versi 1.3.5

{% highlight bash%}
  wget http://rubyforge.org/frs/download.php/60718/rubygems-1.3.5.tgz
  tar xvzf rubygems-1.3.5.tgz
  cd rubygems-1.3.5
  sudo ruby setup.rb
{% endhighlight %}

**Keempat** : ketikan perintah gem -v, jika keluar tampilan,
{% highlight ruby%}
  The program 'gem' can be found in the following packages:
   * rubygems1.8
   * rubygems1.9
  Try: sudo apt-get install
  -bash: gem: command not found
{% endhighlight%}

maka buatlah symlinks dari folder bin ke local di system,
{% highlight ruby%}
  sudo ln -s /usr/bin/gem1.8 /usr/local/bin/gem
  sudo ln -s /usr/bin/ruby1.8 /usr/local/bin/ruby
  sudo ln -s /usr/bin/rdoc1.8 /usr/local/bin/rdoc
  sudo ln -s /usr/bin/ri1.8 /usr/local/bin/ri
  sudo ln -s /usr/bin/irb1.8 /usr/local/bin/irb
{% endhighlight%}

**Kelima** : saatnya menginstal rails, perintah berikut boleh tidak dimasukan --no-rdoc dan --no-ri, versi terbaru ketika tulisan ini dibuat adalah versi 2.3.5,

{% highlight ruby%}
  sudo gem install rails --no-rdoc --no-ri
{% endhighlight%}

proses instalasi ruby on rails basic telah selesai dilakukan, tahapan selanjutnya akan dilanjutkan di tulisan selanjutnya
