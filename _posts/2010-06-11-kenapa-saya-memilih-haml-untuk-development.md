---
layout: post
title: Kenapa Saya Memilih HAML untuk Development
date: 2010-06-11 02:35:06.000000000 +07:00
type: post
published: true
status: publish
categories:
- Rails
tags: []
google_analytics : true
comments  : true
---

sebagai orang yang tidak memiliki latar belakang desain sejujurnya saya sangat kesulitan ketika harus mengorganisasikan CSS kedalam aplikasi yang sedang dibangun oleh tim karena sangat mungkin akan terjadi banyak pengulangan, saya menggunakan compass dengan blueprint sebagai framework-nya dan *it's magic*....*super faboluos*....!

Compass adalah framework yang *awesome* untuk mengorganisasikan CSS, didalamnya saya menggunakan blueprint sebagai CSS framework dengan grid desainnya.

Dikarenakan Compass menggunakan SASS (*Syntactically Awesome Stylesheets*)  yaitu sebuah bahasa yang memiliki sintaks untuk stylesheets, dan HAML (*HTML Abstraction Markup Language*) adalah markup language yang digunakan untuk menggambarkan XHTML secara sederhana dan rapi. Karena Haml adalah *templeting engine* maka sangat mungkin akan memperlambat akses di server, sehingga saya berketetapan untuk meng-*convert*-nya ke html kembali saat stage production.

Setiap orang boleh punya pilihan, pilihan saya jatuh pada haml karena saya lebih nyaman menggunakannya. Kalau ditanya alasannya

1. DRY-ing
2. Konsisten
3. bersahabat dengan mata ….:-)

**Markup should be beautiful!!!**
