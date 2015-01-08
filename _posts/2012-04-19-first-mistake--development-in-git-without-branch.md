---
layout: post
title: "First Mistake : Development In Git Without Branch"
category: Git
tags: [Development, Git]
google_analytics : true
comments  : true
---

Saya pernah punya pengalaman development dengan GIT hanya dengan menggunakan satu branch yaitu branch master, saya berkolaborasi degan lebih dari 8 orang developer. Saat itu semua developer baru switch dari SVN sehingga alam pikirannnya masih diselimuti oleh proses terpusat (centralized) dalam SVN. Saya masih ingat bahwa untuk commit harus menunggu antrian jika ada developer lain sedang commit...hhhmmmmmm.

Yang lebih membuat saya terpana adalah cara kita provide code ke client, code yang disiapkan untuk setiap realese diberikan dalam bentuk ZIP file yang kita upload ke FTP server mereka.

Apa yang kita lakukan tidaklah bodoh tapi stupidd...:-)...bodohnya saya waktu itu. Kenapa saya katakan cara yang stupid,
hal sederhana yang bisa anda bayangkan jika ada bug dalam setiap realese. Apakah client harus menunggu dikirimi ZIP file jika bug atau defect tadi sudah ke-resolve....

Dalam pikiran saya kenapa hal itu bisa terjadi karena pada waktu itu saya tidak paham konsep distributed version control yang diusung oleh git.  Cara git menghandel branching and merging cukup unik. proses untuk membuat branch atau pindah branch tidaklah sulit dan prosesnya cukup cepat. Git memiliki satu directory kerja yang isinya bisa kita ubah-ubah berdasarkan branch dimana kita bekerja dengan kata lain kita tidak membutuhkan directory baru untuk setiap branch yang kita buat.

Sebagai ilustrasi sederhana, secara default saat kita menginisiasi project dengan menggunakan git sebagai version console maka maka kita ada di branch master

		$ git branch
		  * master

<section role="banner">
  <img src="http://learn.github.com/images/branch/step1.png" />
  <sup>sumber http://learn.github.com/images/branch/step1.png</sup>
</section>


C0, C1, C2 adalah daftar riwayat commit


selanjutanya jika kita ingin membuat banch baru dan berpindah ke branch baru maka

		$ git branch experiment
		$ git checkout experiment
		Switched to branch "experiment"
		$ git branch
		* experiment
  	  master

ilustrasinya seperti ini.

<section role="banner">
  <img src="http://learn.github.com/images/branch/step2.png" />
  <sup>sumber http://learn.github.com/images/branch/step2.png</sup>
</section>


Dalam fikiran saya branch yang harus ada dalam setiap proses development adalah

- Realese Branch, Branch yang kita gunakan untuk menandai realese code yang akan dideploy ke production yang kita merge dengan master

- Working Branch, Branch yang digunakan oleh setiap anggota dalam tim. Jika satu task atau story telah selesai member tim bisa merging ke staging branch untuk di test.

- Staging branch, Branch yang digunakan untuk test code sebelum dimerge dengan release.

- Hotfix Branch, branch yang kita gunakan untuk trace bug atau deffect jika ditemukan bug atau deffect dalam suatu realase.

		$ git checkout --track -b release-date origin/release-date



Saya berfikir bahwa implementasi untuk setiap tim atau organisasi akan sangat berbeda, Tetapi nilai moral yang inbgin sya sampaikan adalah jika anda kerja di git pahami branch dan gunakan.


Jika anda ingin memahami lebih lanjut tentang flow dalam Git bisa bisa lihat [git-flow](https://github.com/nvie/gitflow)

Kommentar dan masukan sangat ditunggu agar saya tidak semakin bodoh.
