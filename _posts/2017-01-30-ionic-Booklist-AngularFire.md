---
layout: post
title: App CRUD Ionic dan AngularFire3
categories: [Ionic, angularfire3]
tags: [Ionic, angularfire3]
description: Ionic dan Angularfire.
---

1. [ionic scarp](https://javebratt.com/ionic-2-firebase-3-week-1/)
[ionic paging](https://javebratt.com/firebase-list-pagination/)
[ionic query](https://javebratt.com/query-angularfire2-lists/)
[ionic search](https://javebratt.com/searchbar-firebase/)
[ionic email auth](https://javebratt.com/angularfire2-authentication-ionic/)
[ionic fb login](https://javebratt.com/ionic-2-facebook-login/)
[ionic anynomius login](https://javebratt.com/firebase-anonymous-login-ionic/)
[firebase security db](https://javebratt.com/firebase-security-rules-ionic-apps/)
[upload picture](https://javebratt.com/firebase-storage-ionic-camera/)
[ionic transaction](https://javebratt.com/firebase-transactions-ionic-apps/)
[ionic ?](https://javebratt.com/firebase-objects-ionic-2-app/)

## Membuat App Booklist Realtime dengan Ionic+AngularFire3

> STEP 1

{% highlight yaml %}
$ ionic start BookList blank --v2
Creating an Ionic 2.x app in D:\Tools\Tutorial-Ionic\BookList based on the blank template.

Downloading: https://github.com/driftyco/ionic2-app-base/archive/master.zip
Downloading: https://github.com/driftyco/ionic2-starter-blank/archive/master.zip
Installing npm packages (may take a minute or two)...
-
♬ ♫ ♬ ♫  Your Ionic app is ready to go! ♬ ♫ ♬ ♫

Some helpful tips:

Run your app in the browser (great for initial development):
  ionic serve

Run on a device or simulator:
  ionic run ios[android,browser]

Share your app with testers, and test on device easily with the Ionic View companion app:
  http://view.ionic.io
$ cd BookList
{% endhighlight %}

## Install Plugins
- Install `app-scripts` versi terakhir di dalam folder project `BookList`.

{% highlight yaml %}
$ npm install @ionic/app-scripts@latest --save-dev
$ ionic-hello-world@ D:\Tools\Tutorial-Ionic\BookList
`-- @ionic/app-scripts@1.0.0
{% endhighlight %}

- Install `@types/request@0.0.30`

{% highlight yaml %}
$ npm install @types/request@0.0.30 --save-dev --save-exact
$ ionic-hello-world@ D:\Tools\Tutorial-Ionic\BookList
`-- @types/request@0.0.30
  +-- @types/form-data@0.0.33
  `-- @types/node@6.0.62
{% endhighlight %}

- Install `angularfire2` dan `Firebase`

{% highlight yaml %}
$ npm install firebase angularfire2 --save
ionic-hello-world@ D:\Tools\Tutorial-Ionic\BookList
+-- angularfire2@2.0.0-beta.7
+-- firebase@3.6.7
| +-- base64-url@1.3.3
| +-- base64url@2.0.0
| +-- buffer-equal-constant-time@1.0.1
| +-- dom-storage@2.0.2
| +-- ecdsa-sig-formatter@1.0.7
| +-- faye-websocket@0.9.3
| +-- hoek@2.16.3
| +-- isemail@1.2.0
| +-- joi@6.10.1
| +-- jsonwebtoken@7.1.9
| +-- jwa@1.1.4
| +-- jws@3.1.4
| +-- lodash.once@4.1.1
| +-- moment@2.16.0
| +-- ms@0.7.2
| +-- rsvp@3.2.1
| +-- safe-buffer@5.0.1
| +-- topo@1.1.0
| +-- websocket-driver@0.6.5
| +-- websocket-extensions@0.1.1
| +-- xmlhttprequest@1.8.0
| `-- xtend@4.0.1
`-- UNMET PEER DEPENDENCY rxjs@5.0.0-beta.12

npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@^1.0.0 (node_modules\chokidar\node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.0.17: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"ia32"})

npm WARN angularfire2@2.0.0-beta.7 requires a peer of rxjs@^5.0.1 but none was installed.
{% endhighlight %}

> Edit `app.module.ts` yang berada `/BookList/src/app/app.module.ts` Tambahkan code di bawah :

## Import Modul AngularFire
{% highlight yaml %}
import { AngularFireModule } from 'angularfire2';
{% endhighlight %}

## Membuat Config Firebase

{% highlight yaml %}
// Initialize Firebase
export const firebaseConfig = {
    apiKey: "AIzaSxxxxxxOmAttak_xxxxxxxxnhRTuUU28",
    authDomain: "my-booklist-xxxxx.firebaseapp.com",
    databaseURL: "https://my-booklist-xxxxx.firebaseio.com",
    storageBucket: "my-booklist-xxxxx.appspot.com",
    messagingSenderId: "10xxxxxxx2"
};
{% endhighlight %}

> Edit pada baris `Import` tambahkan code `AngularFireModule.initializeApp(firebaseConfig)` seperti di bawah :

{% highlight yaml %}
imports: [
    IonicModule.forRoot(MyApp),
    AngularFireModule.initializeApp(firebaseConfig)
  ],
{% endhighlight %}

> Edit `home.html` yang berada `/BookList/src/pages/home` menjadi seperti di bawah :

{% highlight yaml %}
<ion-header>
  <ion-navbar>
    <ion-title>
      Ionic Blank
    </ion-title>
        <ion-buttons end>
          <button ion-button icon-only (click)="addSong()">
                <ion-icon name="add"></ion-icon>
          </button>
        </ion-buttons>
  </ion-navbar>
</ion-header>

<ion-content padding>
  The world is your oyster.
  <h2>Book list</h2>
    <ion-list>
        <ion-item *ngFor="let book of books | async">
            {{book.title}}
            {{book.author}}
        </ion-item>
    </ion-list>
</ion-content>
{% endhighlight %}

## Membuat Database di Firebase
login di web https://console.firebase.google.com buka database yang sudah kita buat, buka tab `DATA`
Jika Error pada tab `DATA` Tidak muncul atau kosong. install `firebase-CLI` secara global.

{% highlight yaml %}
$ npm install -g firebase-tools
{% endhighlight %}

- Klik Tab `RULE` akan muncul tampilan di bawah :

{% highlight yaml %}
{
  "rules": {
    ".read": "auth != null",
    ".write": "auth != null"
  }
}
{% endhighlight %}

- Rubah menjadi `true` dan klik `PUBLISH` kembali ke tab `DATA`

{% highlight yaml %}
{
  "rules": {
    ".read": "true",
    ".write": "true"
  }
}
{% endhighlight %}

{% highlight yaml %}
Name : Books value : [{"title" : "My Book", "author": "Tim"}]
{% endhighlight %}

Nama Database : my-booklist-XXXX
Table : Books
index : 0
Variable : 
  - name
  - value

- Setelah membuat variabel di database, saat nya untuk coding di folder project kita. buka `home.html` dan `home.ts`

## Edit `home.ts` 

- Tambahkan import di bawah

{% highlight yaml %}
import { AngularFire, FirebaseListObservable} from 'angularfire2';
{% endhighlight %}

- tambahkan property di dalam `export class HomePage`
{% highlight yaml %}
books: FirebaseListObservable<any>;
{% endhighlight %}

- pada `constructor` tambahkan `angFire: AngularFire` dan edit sedikit

{% highlight yaml %}
  constructor(public navCtrl: NavController, angFire: AngularFire) {
    this.books = angFire.database.list('/Books');  
  }
{% endhighlight %}

`this.books = angFire.database.list('/Books'); ` kode berikut mengambil nilai tabel `Books` yang berada di firebase dengan field `author` dan `title` yang memiliki nilai :
`author` : My Book
`title`  : tipobrata

- isi file `home.ts`

{% highlight yaml %}
import { Component } from '@angular/core';

import { NavController } from 'ionic-angular';
import { AngularFire, FirebaseListObservable } from 'angularfire2';

@Component({
  selector: 'page-home',
  templateUrl: 'home.html'
})
export class HomePage {
//Membuat variabel Books
  books: FirebaseListObservable<any>;

  constructor(public navCtrl: NavController, angFire: AngularFire) {
    this.books = angFire.database.list('/Books');    
  }
}
{% endhighlight %}

- pada file `home.html` rubah bagian `content padding`

{% highlight yaml %}
<ion-content padding>
  The world is your knowloge.
  <h2>Book list</h2>
    <ion-list>
      <ion-item *ngFor="let book of books | async">
        <p>Title  : {{book.title}}</p>
        <p>Author : {{book.author}}</p>
      </ion-item>
    </ion-list>
</ion-content>
{% endhighlight %}

- Refresh Browser `http://localhost:8100/`

> STEP 2

## Membuat `Modal` Tambah Data/Buku

- Edit file `home.ts` pada `import from ionic-angular` tambahkan `AlertController` 

{% highlight yaml %}
import { NavController, AlertController } from 'ionic-angular';
{% endhighlight %}

- pada `constructor` tambahkan `alertCtrl: AlertController`

{% highlight yaml %}
constructor(public navCtrl: NavController, public alertCrtl: AlertController, angFire: AngularFire) {
    this.books = angFire.database.list('/Books'); 
  }
{% endhighlight %}

## Membuat Method `tambah` Data/Buku `addBook`

{% highlight yaml %}
addBook():void {
    let prompt = this.alertCtrl.create({
      title: 'Book Title and Author',
      message: 'enter the book title and author'
    })

    prompt.present();
  }

{% endhighlight %}

Jalankan di browser dan akan muncul tampilan `Modal` seperti di bawah.

## Membuat Form input
untuk membuat form input tambahkan code di bawah, pada baris setelah `message`

{% highlight yaml %}
inputs: [
        {
          name: 'title',
          placeholder: "Judul Buku"
        },
        {
          name: 'author',
          placeholder: "Nama Penulis"
        }
      ],
{% endhighlight %}

## Membuat Button `Cancel` dan `Simpan`
untuk membuat form input tambahkan code di bawah, pada baris setelah `inputs`

{% highlight yaml %}
buttons: [
        {
          text: "Cancel",
          handler: data => {
            console.log("cancel clicked");
          }
        },
        {
          text: "Simpan Buku",
          handler: data => {
            this.books.push({
              title: data.title,
              author: data.author,
            })
          }
        }
      ]
{% endhighlight %}

## Membuat Edit dan Hapus Data

Sebelum membuat edit dan hapus data pertama-tama memahami cara kerja nya terlebih dahulu
- Menambahkan fungsi sliding pada `home.html` agar bisa di geser ke kanan dan ke kiri. serta membuat method/action dan juga menampilkan menu `hapus` dan `edit`
- File yang akan kita akses adalah `home.ts` dan `home.html`

## Edit bagian content `home.html` menjadi seperti di bawah

{% highlight yaml %}
 <ion-content padding>
  <h1>Belajar Ionic</h1>
  <h2>Book list</h2>
    <ion-list>
    <ion-item-sliding *ngFor="let book of books | async">
      <ion-item>
        <p>Title  : {{book.title}}</p>
        <p>Author : {{book.author}}</p>
      </ion-item>
      <ion-item-options side="right">
            <button ion-button color="secondary" (click)="editBook(book)">
                <ion-icon name="md-create">Edit</ion-icon>
            </button>
      </ion-item-options>
      <ion-item-options side="left">
            <button ion-button color="danger" (click)="deleteBook(book.$key)">
                <ion-icon name="md-trash">Hapus</ion-icon>
            </button>
      </ion-item-options>
      </ion-item-sliding>
    </ion-list>
</ion-content>
{% endhighlight %}

## Membuat `method` `Simpan`, `Edit` dan `Hapus` pada `home.ts`

## 1. Fungsi Simpan

{% highlight yaml %}
addBook():void {
    let prompt = this.alertCtrl.create({
      title: 'Judul Buku and Penulis',
      message: 'Masukkan Judul Buku dan Penulis',
      inputs: [
        {
          name: 'title',
          placeholder: "Judul Buku"
        },
        {
          name: 'author',
          placeholder: "Nama Penulis"
        }
      ],
      buttons: [
        {
          text: "Cancel",
          handler: data => {
            console.log("cancel clicked");
          }
        },
        {
          text: "Simpan Buku",
          handler: data => {
            this.books.push({
              title: data.title,
              author: data.author,
            })
          }
        }
      ]
    })

    prompt.present();
  }
{% endhighlight %}

## 2. Fungsi Edit

{% highlight yaml %}
editBook(book):void {
    let prompt = this.alertCtrl.create({
      title: 'Edit Buku',
      message: 'Edit Judul Buku dan Penulis',
      inputs: [
        {
          name: 'title',
          placeholder: book.title
        },
        {
          name: 'author',
          placeholder: book.author
        }
      ],
      buttons: [
        {
          text: "Cancel",
          handler: data => {
            console.log("cancel clicked");
          }
        },
        {
          text: "Simpan Buku",
          handler: data => {
            let newTitle:String = book.title;
            let newAuthor:String = book.author;
            if (data.title != ''){
              newTitle = data.title;
            }
            if(data.author != '') {
              newAuthor = data.author;
            }
            this.books.update(book.$key, {
              title: newTitle,
              author: newAuthor
            })
          }
        }
      ]
    })
    prompt.present();
  }
{% endhighlight %}

## 3. Fungsi Hapus

{% highlight yaml %}
deleteBook(bookID):void {
    let prompt = this.alertCtrl.create({
      title: 'Hapus Buku',
      buttons: [
        {
          text: "Cancel",
          handler: data => {
            console.log("cancel clicked");
          }
        },
        {
          text: "Hapus Buku",
          handler: data => {
            this.books.remove(bookID)
          }
        }
      ]
    })

    prompt.present();
  }
{% endhighlight %}
