---
layout: post
title: Sedikit tentang attr_accessor
date: 2010-02-06 14:26:21.000000000 +07:00
type: post
published: true
status: publish
categories:
- Ruby
tags:
- attr_accessor
- attr_write
google_analytics : true
comments  : true
---

attr_accessor adalah method yang digunakan untuk proses *set* dan *get* dari accessor (pengakases variabel), Sesuai dengan Mantra dari DRY (Don't Repeat Yourself),  dengan menggunakan method ini kita tidak usah repot menduplikasi method yang sama secara berulang-ulang hanya untuk men-*set* variabel  dari method initialize.

Pengetahuan tentang *attr_accessor* dibutuhkan karena adakalanya untuk suatu kebutuhan tertentu method ini tidak kita gunakan, untuk lebih jelasnya saya buat sebuah code sederhana yang lengkap tanpa menggunakan *attr_accessor*.

{% highlight ruby %}
class Orang
  attr_accessor :nama, :kelamin
  attr_writer :nama
  attr_reader :nama
  attr_writer :kelamin
  attr_reader :kelamin

  def initialize(aNama, aKelamin)
    @nama = aNama
    @kelamin = aKelamin
  end

  #set accessor untuk @nama
  def nama=(aNama)
    @nama = aNama
  end

  #get accessor untuk @nama
  def nama
    return @nama
  end

  #set accessor for @kelamin
  def kelamin=(aKelamin)
    @kelamin = aKelamin
  end

  #get accessor untuk @kelamin
  def kelamin
    return @kelamin
  end

end

t = Orang.new("Asep", "Lelaki tulen")
puts(t.nama)
puts(t.kelamin)
{% endhighlight %}

silahkan anda mencobanya dengan melakukan comment pada masing-masing. Saya masukan juga method *attr_writer* dan *attr_reader* yang dapat digunakan untuk set accessor dan get accessor instance variable.

{% highlight ruby %}
class Orang
    attr_writer :nama
    attr_reader :nama
    attr_writer :kelamin
    attr_reader :kelamin

    def initialize(aNama, aKelamin)
      @nama       = aNama
      @kelamin    = aKelamin
    end
end
t = Orang.new("Asep", "Lelaki tulen")
puts(t.nama)
puts(t.kelamin)
{% endhighlight %}

kemudian coba code ini,

{% highlight ruby %}
class Orang
  attr_accessor :nama, :kelamin
  def initialize(aNama, aKelamin)
    @nama       = aNama
    @kelamin    = aKelamin
  end
end
t = Orang.new("Asep", "Lelaki tulen")
puts(t.nama)
puts(t.kelamin)
{% endhighlight %}
