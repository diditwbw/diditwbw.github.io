---
layout: post
title: Membuat App BloggerFire dari Ionic2 dengan Firebase3
categories: [ionic, firebase]
tags: [ionic, firebase]
description: FireBlogger dari Ionic dengan Firebase.
---
## CREATE FIREBLOGGER FROM IONIC WITH FIREBASE

## Buat project `fireblogger`

{% highlight yaml %}
$ ionic start fireblogger --v2
Creating an Ionic 2.x app in D:\Tools\Tutorial-Ionic\bloggerfire based on the tabs template.

Downloading: https://github.com/driftyco/ionic2-app-base/archive/master.zip
Downloading: https://github.com/driftyco/ionic2-starter-tabs/archive/master.zip
Installing npm packages (may take a minute or two)...
\
♬ ♫ ♬ ♫  Your Ionic app is ready to go! ♬ ♫ ♬ ♫

Some helpful tips:

Run your app in the browser (great for initial development):
  ionic serve

Run on a device or simulator:
  ionic run ios[android,browser]

Share your app with testers, and test on device easily with the Ionic View companion app:
  http://view.ionic.io

$ cd blogerfire 
$ ionic serve --lab
{% endhighlight %}

## Install `firebase` ke dalam folder project

{% highlight yaml %}
$ npm install firebase --save
ionic-hello-world@ D:\Tools\Tutorial-Ionic\bloggerfire
`-- firebase@3.6.8
  +-- base64-url@1.3.3
  +-- base64url@2.0.0
  +-- buffer-equal-constant-time@1.0.1
  +-- dom-storage@2.0.2
  +-- ecdsa-sig-formatter@1.0.7
  +-- faye-websocket@0.9.3
  +-- hoek@2.16.3
  +-- isemail@1.2.0
  +-- joi@6.10.1
  +-- jsonwebtoken@7.1.9
  +-- jwa@1.1.4
  +-- jws@3.1.4
  +-- lodash.once@4.1.1
  +-- moment@2.16.0
  +-- ms@0.7.2
  +-- rsvp@3.2.1
  +-- safe-buffer@5.0.1
  +-- topo@1.1.0
  +-- websocket-driver@0.6.5
  +-- websocket-extensions@0.1.1
  +-- xmlhttprequest@1.8.0
  `-- xtend@4.0.1
{% endhighlight %}

## Jalankan typings ke firebase, dengan catatan modul `typings` sudah terinstall global di laptop anda. jika belum terinstalll jalankan `$ npm install -g typings`

{% highlight yaml %}
$ typings install --save firebase
firebase@3.0.5
`-- es6-promise
{% endhighlight %}

## Menambah Font-Awesome di Project Android

copy ke dalam folder `bloggerfire\www\assets` untuk Font-Awesome yang sudah di download -> [Font-Awesome](http://fontawesome.io/#modal-download) 

tambahkan pada file `index.html` di dalam tag `<head>`

{% highlight yaml %}
<link rel="stylesheet" href="assets/font-awesome/css/font-awesome.min.css">
{% endhighlight %}

## Cara Membuat page di ionic

{% highlight yaml %}
$ ionic g page posts
{% endhighlight %}

> *hasil berada di /fireblogger/src/pages*

## Buat pages `login`

{% highlight yaml %}
$ ionic g page login
{% endhighlight %}

## Buat pages `reset-password`

{% highlight yaml %}
$ ionic g page reset-password
{% endhighlight %}

- Isi file -> `/fireblogger/src/app/app.component.ts`
    
{% highlight yaml %}
import { Component } from '@angular/core';
import { Platform } from 'ionic-angular';
import { StatusBar, Splashscreen } from 'ionic-native';

import { TabsPage } from '../pages/tabs/tabs';
import { LoginPage } from '../pages/login/login';
import * as firebase from 'firebase';

@Component({
  templateUrl: 'app.html'
  })
   export class MyApp {
    public rootPage: any;
      constructor(platform: Platform) {
      // Initialize Firebase
      var config = {
      apiKey: "AIxxxxxx4tTWfDWD-xxxxxxxxBQHgDFBjZyvvps",
      authDomain: "meform-xxx.firebaseapp.com",
      databaseURL: "https://meform-xxxx.firebaseio.com",
      storageBucket: "meform-xxx.appspot.com",
      messagingSenderId: "11111111111"
      };
      firebase.initializeApp(config);
      // Merubah form login menjadi di halaman utama
      firebase.auth().onAuthStateChanged((user) => {
        if(user){
          this.rootPage = TabsPage;
            }else {
          this.rootPage = LoginPage;
          }
      });
      platform.ready().then(() => {
      // Okay, so the platform is ready and our plugins are available.
      // Here you can do any higher level native things you might need.
      StatusBar.styleDefault();
        Splashscreen.hide();
        });
      }
}
{% endhighlight %}

Isi file -> `/fireblogger/src/app/app.module.ts`

{% highlight yaml %}
import { NgModule, ErrorHandler } from '@angular/core';
import { IonicApp, IonicModule, IonicErrorHandler } from 'ionic-angular';
import { MyApp } from './app.component';
import { AboutPage } from '../pages/about/about';
import { ContactPage } from '../pages/contact/contact';
import { HomePage } from '../pages/home/home';
import { TabsPage } from '../pages/tabs/tabs';
import { LoginPage } from '../pages/login/login';

  @NgModule({
  declarations: [
   MyApp,
   AboutPage,
   ContactPage,
   HomePage,
   TabsPage,
   LoginPage
   ],
  imports: [
  IonicModule.forRoot(MyApp)
  ],
  bootstrap: [IonicApp],
  entryComponents: [
  MyApp,
  AboutPage,
  ContactPage,
  HomePage,
  TabsPage,
  LoginPage
  ],
  providers: [{provide: ErrorHandler, useClass: IonicErrorHandler}]
})
export class AppModule {}
{% endhighlight %}

- Buat page register
{% highlight yaml %}
ionic g page register
{% endhighlight %}

- Mengganti halaman depan applikasi dengan `Form Login` 
- Membuat form `Login`
- Linking page `login` dengan `register` dan `login.ts`      

{% highlight yaml %}
import { Component } from '@angular/core';
  import { NavController, NavParams, ModalController } from 'ionic-angular';
  import { RegisterPage } from '../register/register'; //Tambahkan baris ini, untuk menampilkan modal dan link ke page register
     
  @Component({
  selector: 'page-login',
  templateUrl: 'login.html'
  })
  export class LoginPage {
  public emailField: any;
  public passwordField: any;
  constructor(public navCtrl: NavController, public navParams: NavParams, private modalCtrl: ModalController) {
  this.emailField = "diditwbw@gmail.com";
  }
  //Fungsi tombol login yang ada di `login.html`
  submitLogin(){
  alert("Hello World");
  }
  //fungsi tombol register untuk menampilkan modal dan link ke form register.
  submitRegister(){ 
  let registerModal = this.modalCtrl.create(RegisterPage);
  registerModal.present();
}
}
{% endhighlight %}

- Pada `/fireblogger/src/app/app.module.ts`, tambahkan import `register`

{% highlight yaml %}
import { RegisterPage } from '../pages/register/register';
{% endhighlight %}

Tambahkan dibawah `@NgModule`

{% highlight yaml %}
RegisterPage
{% endhighlight %}

Tambahkan di bawah `entryComponents`

{% highlight yaml %}
RegisterPage
{% endhighlight %}

## Menutup Modal register

  - Buka file register.html
    
{% highlight yaml %}
<ion-header>
//Buat Toolbar dengan font-awesome
<ion-toolbar>
  <ion-title><i class="fa fa-user" aria-hidden="true"></i>Register</ion-title>
  //pasang tombol klik untuk close dan buat fungsi untuk memanggil
    <ion-buttons start (click)="closeRegisterPage()">
  //tombol silang di kanan atas
    <button><ion-icon name="md-close"></ion-icon></button>
        </ion-buttons>
</ion-toolbar>
</ion-header>
<ion-content padding>
  //tombol untuk kembali ke halaman login dengan memanggil fungsi closeRegisterPage()
<button (click)="closeRegisterPage()"> Return To Login</button>
</ion-content>
{% endhighlight %}

- Buka file register.ts

{% highlight yaml %}
          import { Component } from '@angular/core';
          import { NavController, NavParams, *ViewController* } from 'ionic-angular';
          @Component({
            selector: 'page-register',
            templateUrl: 'register.html'
          })
          export class RegisterPage {
            constructor(public navCtrl: NavController, public navParams: NavParams, *private viewCtrl: ViewController*) {}
            //fungsi untuk menutup form modal register
            closeRegisterPage(){
              this.viewCtrl.dismiss();
            }
          }
{% endhighlight %}

## Perhatikan yang bertanda `*` wajib di isi, berikut keterangannya :
      
  - `ViewController` : tambahkan import untuk menjalankan property dari  `private viewCtrl: ViewController` pada constructor.
  - `private viewCtrl: ViewController` : Menambahkan property `ViewController` pada constructor untuk menjalankan `viewCtrl` agar bisa di gunakan.
  - `viewCtrl` : bagian dari `property ViewController` untuk menutup form modal dengan memanggil `method dismiss`

## Redirect dari page `register` ke `Reset Password`  

- Tambahkan tombol reset password di bawah tombol `closeRegisterpage()` pada `register.html`
      
{% highlight yaml %}
<button (click)="redirectToResetPage()"> Reset Password</button>
{% endhighlight %}

- Tambahkan `alias` dari `reset-password` pada halaman `register.ts`

{% highlight yaml %}
import { ResetPasswordPage } from '../reset-password/reset-password';
{% endhighlight %}

- Buat fungsi `redirectToResetpage()` pada `register.ts`
    
{% highlight yaml %}
redirectToResetpage(){
  this.navCtrl.push(ResetPasswordPage);
}
{% endhighlight %}

- `Javascript Object`, membuat javascript object seperti kode di bawah dan mengambil data tersebut, edit `fungsi redirectToResetPage` menjadi seperti di bawah :
    
{% highlight yaml %}
redirectToResetPage(){
    this.navCtrl.push(ResetPasswordPage, {
      name: 'Didit Wibowo',
      viewer: 'Good Boy',
      randNumber: '666'
    });
}
{% endhighlight %}

- pada `reset-password.ts` tambahkan import `Navparams`
{% highlight yaml %}
import { NavController, NavParams } from 'ionic-angular';
{% endhighlight %}

- Pada `constructor` rubah menjadi seperti di bawah. 

{% highlight yaml %}
constructor(private navCtrl: NavController, private navParams: NavParams) {
    alert(this.navParams.get('name'));
  }
{% endhighlight %}

  - `private navParams: NavParams` : untuk mengambil javascript object harus menggunakan property `NavParams` pada constructor.
  - `alert(this.navParams.get('name'));` : kode bagaimana mengambil nilai nama dari fungsi atau method `redirectToResetPage` yang berisi nilai yang sudah di definisikan.

- Agar Applikasi bisa berjalan pada `register.ts` tambahkan import `Navparams` pada baris `ionic-angular`.
{% highlight yaml %}
import { NavController, NavParams, ViewController } from 'ionic-angular';
{% endhighlight %}

- masih di `register.ts` tambahkan juga pada baris `constructor` rubah menjadi seperti di bawah.
{% highlight yaml %}
constructor(private navCtrl: NavController, private navParams: NavParams, private viewCtrl: ViewController) {}
{% endhighlight %}

## Jika kita ingin menampilkan/memangil `javascript object` pada halaman *.html*, berikut langkahnya.
> Cara 1: Buka `reset-password.ts`

Tambahkan `public username: any;` di atas `constructor`. rubah kode di bawah menjadi :
{% highlight yaml %}
//Sebelum
alert(this.navParams.get('name'));

//Sesudah
this.username = this.navParams.get('name'));
{% endhighlight %}

> Buka `reset-password.html`

{% highlight yaml %}
<ion-content padding>
<h1> {{username}} </h1>
</ion-content>
{% endhighlight %}

> Cara 2 : Atau bisa juga seperti ini, pada `register.ts`

{% highlight yaml %}
redirectToResetPage(){

    var allContents = {
    name: 'Didit Wibowo',
    viewer: 'Good Boy',
    randNumber: '666'
    }

    this.navCtrl.push(ResetPasswordPage, {
      userdetails: allContents});
  }
{% endhighlight %}

> Edit pada `reset-password.ts`

{% highlight yaml %}
public username: any;
  constructor(private navCtrl: NavController, private navParams: NavParams) {
    this.username = this.navParams.get('userdetails').name;
  }
{% endhighlight %}

## Providers and Services

>Cara update global `typescripts` dengan versi terbaru
>$ npm update -g typescript

Buat folder dan file  `bloggerfire\src\providers\users-services.ts` dengan perintah di bawah lihat Angular2 [dependency-injection](https://angular.io/docs/ts/latest/guide/dependency-injection.html)

```
$ ionic g provider users-services
```

## Http Json Requests

Ok kita akan ambil data json dari sebuah web, buka link [randomuser](https://randomuser.me/api/?results=1) dan tampilkan di browser.

Buat fungsi `loadUser()` berikut kode lengkap `users-services.ts`

```
import { Injectable } from '@angular/core';
import { Http } from '@angular/http';
import 'rxjs/add/operator/map';

@Injectable()
export class UsersServices {

private data: any;
  constructor(public http: Http) {
    //console.log('Hello UsersServices Provider');
  }
  // buat fungsi loadUser
  loadUser(number){
    if(this.data){
        return Promise.resolve(this.data);
    }
    return new Promise(resolve => {
      this.http.get('https://randomuser.me/api/?results='+number)
        .map(res => res.json())
        .subscribe(data => {
          this.data = data.results;
          resolve(this.data);
        })
    })
  }
}
```

> Buka  `login.ts` tambahkan 

Tambahkan Import di bawah
```
import { UsersServices } from '../../providers/users-services';
```

pada `@Component` tambahkan :
```
providers: [UsersServices]
```

Tambahkan pada Class `LoginPage`  
```
    private users = [];
    private usersList: any;
```

Pada baris `constructor`
```
private usersService: UsersServices{
  this.listOurUsers();
}
```

Buat fungsi `listOurUsers()`

```
listOurUsers(){
    this.usersService.loadUser(10)
    .then(data => {
      this.usersList = data;
    })
  }
```

> Edit login.html tambahkan di bawah button `register`

```
<ion-list>
        <p>Latest User</p>
        <ion-item *ngFor="let user of usersList">
            <ion-label>{{user.name.first}} {{user.name.last}}</ion-label>
        </ion-item>
    </ion-list>
```

Begitulah cara menampilkan data `json` dengan ionic.

## User Registration
