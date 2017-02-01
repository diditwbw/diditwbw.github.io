---
layout: post
title: Pull dan Push jekyll Heroku
categories: [general, jekyll, heroku]
tags: [jekyll, heroku]
description: jekyll on heroku post.
---

Bagaimana menjalankan pull dan push applikasi yang sudah ada di `heroku`, contoh kasus : pada blog `jekyll` yang sudah terpasang di `heroku` bisa berfungsi untuk update artikel atau ganti theme, saat kita sedang menggunakan komputer lain dan pastinya terkoneksi internet.

- Tools yang di butuhkan :

	- [Heroku CLI][heroku-CLI]

	- [Git][G-it]

	- [Jekyll][jeky-ll]

	- [notepad++][note-pad]

>**Step :**

**Login Ke heroku**

{% highlight yaml %}
$heroku login
{% endhighlight %}


**Cloning applikasi dari heroku ke local pc/laptop**

{% highlight yaml %}
$ heroku git:clone -a nama_app
Cloning into 'nama_app'...
remote: Counting objects: 82, done.
remote: Compressing objects: 100% (55/55), done.
remote: Total 82 (delta 29), reused 0 (delta 0)
Unpacking objects: 100% (82/82), done.
{% endhighlight %}


**Masuk ke folder nama_app**

{% highlight yaml %}
$ cd nama_app/
{% endhighlight %}


**Cek repository heroku yang ada di repository local kita, apakah sudah benar nama_app nya.**

{% highlight yaml %}
$ git remote -v
heroku  https://git.heroku.com/nama_app.git (fetch)
heroku  https://git.heroku.com/nama_app.git (push)
{% endhighlight %}


**Jika ada Perubahan pada blog jalankan :**

{% highlight yaml %}
$ jekyll build
{% endhighlight %}


**Simpan ke repository local**

{% highlight yaml %}
$ git add .
$ git commit -m "konfig heroku"
{% endhighlight %}


**Push / deployment ke heroku**

{% highlight yaml %}
$ git push heroku master
{% endhighlight %}


**Buka url untuk melihat hasilnya**

`https://nama_app.herokuapp.com/`


{% highlight yaml %}
$ git push heroku master
Counting objects: 16, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (11/11), done.
Writing objects: 100% (16/16), 4.78 KiB | 0 bytes/s, done.
Total 16 (delta 7), reused 0 (delta 0)
remote: Compressing source files... done.
remote: Building source:
remote:
remote: -----> PHP app detected
remote: -----> Bootstrapping...
remote: -----> Installing platform packages...
remote:        NOTICE: No runtime required in composer.lock; using PHP ^5.5.17
remote:        - apache (2.4.20)
remote:        - nginx (1.8.1)
remote:        - php (5.6.28)
remote: -----> Installing dependencies...
remote:        Composer version 1.2.2 2016-11-03 17:43:15
remote: -----> Preparing runtime environment...
remote: -----> Checking for additional extensions to install...
remote: -----> Discovering process types
remote:        Procfile declares types -> web
remote:
remote: -----> Compressing...
remote:        Done: 14.7M
remote: -----> Launching...
remote:        Released v7
remote:        https://nama_app.herokuapp.com/ deployed to Heroku
remote:
remote: Verifying deploy... done.
To https://git.heroku.com/nama_app.git
7caef36..fb23fdf  master -> master
{% endhighlight %}



>**Beberapa contoh Perintah heroku CLI :**

**Remote akses ke Applikasi di heroku**

{% highlight yaml %}
$ heroku git:remote -a nama_app
set git remote heroku to https://git.heroku.com/nama_app.git
{% endhighlight %}


**melihat applikasi yang sudah di buat di heroku :**


{% highlight yaml %}
$ heroku apps
{% endhighlight %}


**Melihat Informasi applikasi yang ada di heroku**


{% highlight yaml %}
$ heroku apps:info
{% endhighlight %}


**Melihat Informasi applikasi tertentu di heroku**


{% highlight yaml %}
$ heroku apps:info --app nama_app
=== nama_app
Dynos:         web: 1
Git URL:       https://git.heroku.com/nama_app.git
Owner:         nama_app@nama_app.com
Region:        us
Repo Size:     58 KB
Slug Size:     150 MB
Stack:         cadar-14
Web URL:       https://nama_app.herokuapp.com/
{% endhighlight %}


**Buat applikasi di heroku**

{% highlight yaml %}
$ heroku create nama_app
{% endhighlight %}


[heroku-CLI]: https://s3.amazonaws.com/assets.heroku.com/heroku-toolbelt/heroku-toolbelt.exe
[G-it]: https://git-scm.com/download/win
[jeky-ll]: https://jekyllrb.com/docs/installation/
[note-pad]: https://notepad-plus-plus.org/