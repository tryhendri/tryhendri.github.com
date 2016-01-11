---
layout: post
title: Tips Aman Development Menggunakan Git
date: 2010-01-01 19:10:21.000000000 +07:00
type: post
published: true
status: publish
categories:
- GIT
tags: []
google_analytics : true
comments  : true
---

Tulisan ini dimaksudkan untuk mengingat setiap tahapan yang hampir setiap kali diulang ketika mengupdate source code di Git, skenario ini adalah standard menurut penulis yang sangat mungkin setiap group atau kelompok coder memiliki cara masing-masing untuk berkolaborasi dalam satu proyek.

langkah-langkah standard yang biasa saya lakukan adalah :

membuat cabang atau *branch*
{% highlight bash %}
git checkout -b
{% endhighlight %}

lakukakan *commit* untuk
{% highlight bash %}
git add .
git commit -m "tuliskan pesan agar diperhatikan oleh anggota kelompok lain"
{% endhighlight %}

masuklah ke master
{% highlight bash %}
git checkout master
{% endhighlight %}

lakukan merge dengan branch
{% highlight bash %}
git merge "nama_branch"
{% endhighlight %}

masukan perubahan ke server git
{% highlight bash %}
git push origin
{% endhighlight %}

delete branch yang tadi kita buat
{% highlight bash %}
git branch -d "nama_branch"
{% endhighlight %}

Perlu saya tegaskan bahwa setiap grup developer punya cara masing-masing untuk mengkomunikasikan setiap perubahan yang dibuat oleh setiap anggotanya
