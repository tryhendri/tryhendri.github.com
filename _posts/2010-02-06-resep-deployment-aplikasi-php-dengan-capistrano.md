---
layout: post
title: Resep Deployment Aplikasi PHP dengan Capistrano
date: 2010-02-06 05:48:48.000000000 +07:00
type: post
published: true
status: publish
categories:
- Deployment
tags:
- Capistrano
- Deployment
- FTPSERVER
google_analytics : true
comments  : true
---
Saya pernah diminta bantuan oleh temen untuk meng-*upload* aplikasi PHP yang dia buat dengan menggunakan aplikasi FTP Server ke server yang dia miliki. tapi entah mengapa selalu saja gagal, kalau tidak salah besar filenya sekitar 23 MB, ukuran yang besar menurut saya untuk aplikasi web, tapi saya maklum karena teman saya ini masih menggunakan  table untuk membuat aplikasinya. padahal cara ini  sudah ditinggalkan sekitar 5-10 tahun yang lalu, saat ini cara yang digunakan adalah *tablesles* dengan CSS-nya.

Sampai tulisan ini diturunkan, saya masih belum melihat kemunculan aplikasinya di url-nya. Saya hanya ingin mengajukan usul pada temen saya, gimana kalau menggunakan Capistrano aplikasi ringan yang sangat powerfull untuk deployment.

ini adalah resep dasar yang bisa dikembangkan,

{% highlight ruby %}
  set :application, "Nama aplikasi" #akan dibuatkan folder sesuai nama aplikasi
  set :repository,  "alamat_repository" # `accurev`, `bzr`, `cvs`, `darcs`, `git`, `mercurial`, `perforce`, `subversion` or `none`

  set :domain, "domain_name"  //bisa dimasukan IP address server
  #  `accurev`, `bzr`, `cvs`, `darcs`, `git`, `mercurial`, `perforce`, `subversion` or `none`
  # your SCM below:
  # contoh dibawah saya pake GIT
  set :scm, :git
  set :scm_checkout, "master"

  # SSH Settings
  set :user, "username"
  set :password, "password_username"
  set :deploy_via, :remote_cache
  role :web, domain                          # Your HTTP server, Apache/etc
  role :app, domain                          # This may be the same as your `Web` server
  role :db,  domain, :primary => true # This is where Rails migrations will run
  role :db,  domain

  set :deploy_to, "/srv/www/" #alamat folder yang bisa diakses oleh serverHost
  set :document_root, "/srv/www/" #alamat folder yang bisa diakses oleh serverHost
  # namespace :deploy do
  #   task :start {}
  #   task :stop {}
  #   task :restart, :roles => :app, :except => { :no_release => true } do
  #     run "#{try_sudo} touch #{File.join(current_path,'tmp','restart.txt')}"
  #   end
  # end<
  namespace :deploy do
    task :update do
      update_code
      symlink
    end
  task :finalize_update do
    run "chmod -R g+w #{releases_path}/#{release_name}"
  end
  task :symlink do
      run "ln -nfs #{current_release} #{deploy_to}/#{current_dir}"
      run "ln -nfs #{deploy_to}/#{current_dir} #{document_root}"
    end
    task :migrate do
      # nothing
    end
    task :restart do
      # nothing
    end
  end
{% endhighlight %}

<p>jika tertarik silahkan dicoba, dijamin lebih memuaskan daripada menggunakan aplikasi ftpserver, untuk lebih mendalaminya silahkan berkunjung ke <a class="wpGallery" href="http://www.capify.org" target="_blank">sini</a></p>
