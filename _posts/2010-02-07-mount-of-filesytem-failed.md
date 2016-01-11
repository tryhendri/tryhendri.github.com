---
layout: post
title: Mount of Filesytem Failed
date: 2010-02-07 04:01:57.000000000 +07:00
type: post
published: true
status: publish
categories:
- Ubuntu
tags:
- mount
google_analytics : true
comments  : true
---

    Mount of filesystem failed.
    A maintenance shell will now be started.
    CONTROL-D will terminate this shell and retry.
    root@server-desktop:


Pagi-pagi dah dapat error gak bisa booting ke system karena directory system unmount akibat listrik mati saat komputer lagi nyala. dengan dua langkah saja, alhamdulillah bisa selesai.
{% highlight bash%}
    sudo fdisk -l
{% endhighlight %}

kemudian dilanjutkan dengan

{% highlight bash%}
sudo fsck.ext2 /dev/sdax
{% endhighlight %}


ext2 disesuaikan dengan type file system bisa ext3 atau ext4, sedangkan untuk x adalah urutan filesystem di hardisk yang digunakan bisa 1,2,3,...dst
