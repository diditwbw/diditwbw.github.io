---
layout: post
title: Hosting Angular2 ke Firebase
categories: [angular2, firebase]
tags: [angular2, firebase]
description: Hosting firebase.
---

## CARA HOSTING ANGULAR2 KE FIREBASE

# Hosting angular di firebase
> STEP 1
> Buat Project dengan angular-cli

{% highlight yaml %}
$ ng new fbangular
$ cd fbangular
$ ng serve

Buka http://localhost:4200/
{% endhighlight %}

# Cara Build applikasi angular ke production
{% highlight yaml %}
$ ng build --prod
{% endhighlight %}

# Buat Project di firebase
> Cara Install `firebase-tool`

{% highlight yaml %}
$ npm install -g firebase-tools

D:\Tools\Tutorial-Angular\Hosting\fbangular>ng build --prod
fallbackLoader option has been deprecated - replace with "fallback"
loader option has been deprecated - replace with "use"
fallbackLoader option has been deprecated - replace with "fallback"
loader option has been deprecated - replace with "use"
fallbackLoader option has been deprecated - replace with "fallback"
loader option has been deprecated - replace with "use"
fallbackLoader option has been deprecated - replace with "fallback"
loader option has been deprecated - replace with "use"
 10% building modules 7/9 modules 2 active ...r\node_modules\@angular\core\index.js(node:3268) DeprecationWarning: loaderUtils.parseQuery() received a non-string v
alue which can be problematic, see https://github.com/webpack/loader-utils/issues/56
parseQuery() will be replaced with getOptions() in the next major version of loader-utils.
Hash: 4cb5dc6b645ed2e4dadb
Time: 43737ms
chunk    {0} main.7a96c1f4a43c7d1245ce.bundle.js (main) 4.33 kB {2} [initial] [rendered]
chunk    {1} styles.d41d8cd98f00b204e980.bundle.css (styles) 1.69 kB {3} [initial] [rendered]
chunk    {2} vendor.0882860df152b7f18b6a.bundle.js (vendor) 2.61 MB [initial] [rendered]
chunk    {3} inline.1d8774ce4c78ba727711.bundle.js (inline) 0 bytes [entry] [rendered]
{% endhighlight %}

# Login ke Firebase

{% highlight yaml %}
$ firebase login

D:\Tools\Tutorial-Angular\Hosting\fbangular>firebase login
? Allow Firebase to collect anonymous CLI usage information? No

Visit this URL on any device to log in:
https://accounts.google.com/o/oauth2/auth?client_id=563584335869-fgrhgmd47bqnekij5i8b5pr03ho849e6.apps.googleusercontent.com&scope=email%20openid%20https%3A%2F%2Fw
ww.googleapis.com%2Fauth%2Fcloudplatformprojects.readonly%20https%3A%2F%2Fwww.googleapis.com%2Fauth%2Ffirebase&response_type=code&state=212016514&redirect_uri=http
%3A%2F%2Flocalhost%3A9005

Waiting for authentication...

+  Success! Logged in as xxxx@gmail.com

{% endhighlight %}

## Init project firebase

{% highlight yaml %}
$ firebase init
D:\Tools\Tutorial-Angular\Hosting\fbangular>firebase init

     ######## #### ########  ######## ########     ###     ######  ########
     ##        ##  ##     ## ##       ##     ##  ##   ##  ##       ##
     ######    ##  ########  ######   ########  #########  ######  ######
     ##        ##  ##    ##  ##       ##     ## ##     ##       ## ##
     ##       #### ##     ## ######## ########  ##     ##  ######  ########

You're about to initialize a Firebase project in this directory:

  D:\Tools\Tutorial-Angular\Hosting\fbangular

? Are you ready to proceed? (Y/n)y
{% endhighlight %}

{% highlight yaml %}
? Are you ready to proceed? Yes
? What Firebase CLI features do you want to setup for this folder? (Press <space> to select)
>(*) Database: Deploy Firebase Realtime Database Rules
 (*) Hosting: Configure and deploy Firebase Hosting sites

? Are you ready to proceed? Yes
? What Firebase CLI features do you want to setup for this folder? Database: Deploy Firebase Realtime Database Rules, Hosting: Configure and deploy Firebase Hosting sites
{% endhighlight %}

# Project Setup
> Pilih `fbangular (fbangular-e5a57)`

{% highlight yaml %}
=== Project Setup

First, let's associate this project directory with a Firebase project.
You can create multiple project aliases by running firebase use --add,
but for now we'll just set up a default project.

? What Firebase project do you want to associate as default? (Use arrow keys)
  [don't setup a default project]
->fbangular (fbangular-e5a57)
  my-booklist (my-booklist-c8d22)
  meform (meform-61c77)
  [create a new project]
{% endhighlight %}

# Database Setup 
> Jika muncul seperti tampilan di bawah, tekan `enter`

{% highlight yaml %}
=== Database Setup

Firebase Realtime Database Rules allow you to define how your data should be
structured and when your data can be read from and written to.

? What file should be used for Database Rules? (database.rules.json)
{% endhighlight %}

# Hosting setup

{% highlight yaml %}
=== Hosting Setup

Your public directory is the folder (relative to your project directory) that
will contain Hosting assets to be uploaded with firebase deploy. If you
have a build process for your assets, use your build's output directory.

? What do you want to use as your public directory? dist
? Configure as a single-page app (rewrite all urls to /index.html)? Yes
? File dist/index.html already exists. Overwrite? No
i  Skipping write of dist/index.html

i  Writing configuration info to firebase.json...
i  Writing project information to .firebaserc...

+  Firebase initialization complete!
{% endhighlight %}

# Firebase Deploy

{% highlight yaml %}
$ firebase deploy

=== Deploying to 'fbangular-e5a57'...

i  deploying database, hosting
+  database: rules ready to deploy.
i  hosting: preparing dist directory for upload...
Uploading: [======                                  ] 14%+  hosting: dist folder uploaded successfully
+  hosting: 7 files uploaded successfully
i  starting release process (may take several minutes)...

+  Deploy complete!

Project Console: https://console.firebase.google.com/project/fbangular-e5a57/overview
Hosting URL: https://fbangular-e5a57.firebaseapp.com
{% endhighlight %}

# Buka pada browser
{% highlight yaml %}
https://fbangular-e5a57.firebaseapp.com
{% endhighlight %}

## Angular2 connect to firebase with angularfire2

> Masuk ke firebase console dan buat tabel seperti di bawah

{% highlight yaml %}
{
  "branch" : {
    "1" : "pemuda",
    "2" : "pkl",
    "3" : "prj"
  }
}
{% endhighlight %}

- masuk ke folder project angular yang sudah kita buat lakukan install `firebase` dan `angularfire` :

{% highlight yaml %}
$ npm install firebase angularfire2 --save
{% endhighlight %}

untuk cek versi `angularfire` dan `firebase` yang di gunakan bisa di lihat di `package.json` pada folder project.

## Koneksi ke Firebase 
> Buat File `firebase.config.ts` dalam folder `\fbangular\src\environments\`

{% highlight yaml %}
export const firebaseConfig = {
    apiKey: "AIzxxxxxxxxxxxEfmrVGw2ADu9lez9L2EM",
    authDomain: "fbangular-xxxx.firebaseapp.com",
    databaseURL: "https://fbangular-xxx.firebaseio.com",
    storageBucket: "fbangular-xxxx.appspot.com"
}
{% endhighlight %}

> Buka dan edit `fbangular\src\app\app.module.ts` import 2 module di bawah :

{% highlight yaml %}
import { AngularFireModule } from 'angularfire2';
import { firebaseConfig } from './../environments/firebase.config';

imports: [
    BrowserModule,
    FormsModule,
    HttpModule,
    AngularFireModule.initializeApp(firebaseConfig)
  ],
{% endhighlight %}

> Buka dan edit `fbangular\src\app\app.component.ts` ketikkan kode di bawah :

{% highlight yaml %}
import { Component } from '@angular/core';
import { AngularFire, FirebaseListObservable } from 'angularfire2';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'app works!';

branchs: FirebaseListObservable<any[]>

  constructor(private af: AngularFire){
    this.branchs = af.database.list('/branch');
  }
}
{% endhighlight %}

> Buka dan edit `fbangular\src\app\app.component.html` ketik kode di bawah :

{% highlight yaml %}
<h1>
    {{title}}
    <ul>
        <li *ngFor="let branch of branchs | async">
            `{branch.$key}: {branch.$value}`
        </li>
    </ul>
</h1>
{% endhighlight %}

> Sekian dan Terima Kasih