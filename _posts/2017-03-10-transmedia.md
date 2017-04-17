---
layout: post
title: Belajar Transmedia
categories: [angular2, firebase]
tags: [angular2, firebase]
description: Belajar Transmedia
---

# Transmedia

```javascript
ng new tokoonline
```

```
npm install firebase angularfire2 --save
```

```
npm install angular2-flash-messages --save
```

* Membuat Component home, Masuk directory `components` jalankan `ng g component home` akan terbentuk home dan file lainnya.

```
D:\Tools\Tutorial-Angular\tokoonline>cd src\app\components

D:\Tools\Tutorial-Angular\tokoonline\src\app\components>ng g component home
installing component
  create src\app\components\home\home.component.css
  create src\app\components\home\home.component.html
  create src\app\components\home\home.component.spec.ts
  create src\app\components\home\home.component.ts
  update src\app\app.module.ts

```

* Membuat Component listings

```
D:\Tools\Tutorial-Angular\tokoonline\src\app\components>ng g component listings
installing component
  create src\app\components\listings\listings.component.css
  create src\app\components\listings\listings.component.html
  create src\app\components\listings\listings.component.spec.ts
  create src\app\components\listings\listings.component.ts
  update src\app\app.module.ts
```

* Membuat Component navbar

```
D:\Tools\Tutorial-Angular\tokoonline\src\app\components>ng g component navbar
installing component
  create src\app\components\navbar\navbar.component.css
  create src\app\components\navbar\navbar.component.html
  create src\app\components\navbar\navbar.component.spec.ts
  create src\app\components\navbar\navbar.component.ts
  update src\app\app.module.ts
```

* Membuat Component listing

```
D:\Tools\Tutorial-Angular\tokoonline\src\app\components>ng g component listing
installing component
  create src\app\components\listing\listing.component.css
  create src\app\components\listing\listing.component.html
  create src\app\components\listing\listing.component.spec.ts
  create src\app\components\listing\listing.component.ts
  update src\app\app.module.ts
```

* Membuat Component add-listing

```
D:\Tools\Tutorial-Angular\tokoonline\src\app\components>ng g component add-listing
installing component
  create src\app\components\add-listing\add-listing.component.css
  create src\app\components\add-listing\add-listing.component.html
  create src\app\components\add-listing\add-listing.component.spec.ts
  create src\app\components\add-listing\add-listing.component.ts
  update src\app\app.module.ts
```

* Membuat Component edit-listing

```
D:\Tools\Tutorial-Angular\tokoonline\src\app\components>ng g component edit-listing
installing component
  create src\app\components\edit-listing\edit-listing.component.css
  create src\app\components\edit-listing\edit-listing.component.html
  create src\app\components\edit-listing\edit-listing.component.spec.ts
  create src\app\components\edit-listing\edit-listing.component.ts
  update src\app\app.module.ts
```


## MEMBUAT ROUTES

* Buka file `app.module.ts` tambahkan baris di bawah :

Import `RouterModule dan Routes`
```
import { RouterModule, Routes} from '@angular/router';
```

* Tambahkan `RouterModule.forRoot(appRoutes)` pada baris import

```
  imports: [
    BrowserModule,
    FormsModule,
    HttpModule,
    RouterModule.forRoot(appRoutes)
  ]
```

* Masih di `app.module.ts` Tambahkan `Const`

```
const appRoutes: Routes = [
  {path:'', component: HomeComponent},
  {path:'listings', component: ListingsComponent},
]
```

* Edit `app.component.ts` dan tambahkan baris di bawah

```
<router-outlet></router-outlet>
```

## Membuat Navbar

* Edit `app.component.html` dan tambahkan baris di bawah

```
<app-navbar></app-navbar>
<div class="container">
    <router-outlet></router-outlet>
</div>
```

Buka link untuk mapping css [bootswatch](https://bootswatch.com/cerulean/bootstrap.min.css) untuk template 

* Pada `index.html` tambahkan `bootstrap.min.css` baris di bawah :

```
<link rel="stylesheet" href="https://bootswatch.com/cerulean/bootstrap.min.css">
```

* Buka [bootstraps](http://getbootstrap.com/examples/starter-template/) copy sample navbar 
* Buka dan edit  `navbar.component.html`

```
<nav class="navbar navbar-inverse">
    <div class="container">
        <div class="navbar-header">
            <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
            <span class="sr-only">Toggle navigation</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
            <a class="navbar-brand" href="#">Brillie</a>
        </div>
        <div id="navbar" class="collapse navbar-collapse">
            <ul class="nav navbar-nav">
                <li>
                    <a [routerLink]="['/']">Home</a></li>
                <li>
                    <a [routerLink]="['/listings']">Listings</a></li>
                <li>
                    <a [routerLink]="['/about']">About</a></li>
            </ul>
        </div>
        <!--/.nav-collapse -->
    </div>
</nav>
```

* Untuk membuat halaman atau page, di angular2 contoh halaman about :
Dalam folder project jalan kan command untuk membuat component `about` 

```
$ ng g component about
```

* Buka `app.module.ts` dan edit tambahkan import component about :

```
import { AboutComponent } from './components/about/about.component';
```

* Pada baris `@NgModule` Tambahkan `AboutComponent` :

```
@NgModule({
    description: [
    AboutComponent
    ]
    });
```

* Pada Baris `const appRoutes` tambahkan :

```
const appRoutes: Routes = [
{path:'about', component: AboutComponent},{path:'about', component: AboutComponent},
]
```

* Tes dan lakukan di browser `http://localhost:4200`

* Untuk menambahkan menu login tambahkan coe di bawah :

```
<ul class="nav navbar-nav navbar-right">
<li><a href="">Login</a></li>
</ul>
```

## Firebase Setup

* Buat akun di google firebase, buka file `app.module.ts` 

Import Component `firebase`

```
import { AngularFireModule } from 'angularfire2';
```

isi firebaseConfig sesuai dengan project yang ada di firebase

```
export const firebaseConfig = {
    apiKey: "AIzaSyDhcMH0FtT5NSIniXfKoKp5pl_t4FZ7LxM",
    authDomain: "tokoonline-d0435.firebaseapp.com",
    databaseURL: "https://tokoonline-d0435.firebaseio.com",
    storageBucket: "tokoonline-d0435.appspot.com",
    messagingSenderId: "88790464134"
};
```

```
imports: [
AngularFireModule.initializeApp(firebaseConfig),
],
```

## Membuat Service Firebase

masuk ke dalam folder `/src/app/services` 

```
\src\app\services>ng g service firebase
installing service
  create src\app\services\firebase.service.spec.ts
  create src\app\services\firebase.service.ts
  WARNING Service is generated but not provided, it must be provided to be used
```

* Buka `firebase.service.ts` tambahkan import firebase :

```
import { AngularFire, FirebaseListObservable } from 'angularfire2';
```

tambahkan constructor seperti kode di bawah :

```
constructor(private af: AngularFire) { }
```

* Tambahkan listings

```
listings: FirebaseListObservable<any[]>
```

* Untuk mendapatkan data dari fire base tambahkan kode di bawah : 

```
getListings(){
    this.listings = this.af.database.list('/listings') as FirebaseListObservable<Listing[]>
    return this.listings;
  }
```

* Diatas Constructor tambahkan kode di bawah:

```
listings: FirebaseListObservable<any[]>
```

* Berikut kode lengkap `firebase.service.ts`

```
import { Injectable } from '@angular/core';
import { AngularFire, FirebaseListObservable } from 'angularfire2';

@Injectable()
export class FirebaseService {

  listings: FirebaseListObservable<any[]>
  constructor(private af: AngularFire) { }

  getListings(){
    this.listings = this.af.database.list('/listings') as FirebaseListObservable<Listing[]>
    return this.listings;
    }
  }
  interface Listing{
    $key?: string;
    $title?: string;
    $type?: string;
    $image?: string;
    $city?: string;
    $owner?: string;
    $bedrooms?: string;
}
```

* Selesai koding di firebase.service.ts, buka `app.module.ts`

```
import { FirebaseService } from './services/firebase.service';
```

* Tambahkan baris provider seperti di bawah

```
providers: [FirebaseService],
```

> Seperti itu cara setting `firebase.config.ts` selanjutnya kita akan menggunakan service `FirebaseService` ke component lainnya.


## Component Listings
Ok sekarang kita akan menggunakan `FirebaseService` pada `Listings` component
* Buka `listings.component.ts` tambahkan import `FirebaseService` seperti kode di bawah :

```
import { FirebaseService } from '../../services/firebase.service';
```

* Pada `Constructor` tambahkan kode di bawah :

```
export class ListingsComponent implements OnInit {
  listings: any;
  constructor(private firebaseService: FirebaseService) { }

  ngOnInit() {
    this.firebaseService.getListings().subscribe(listings => {
      console.log(listings);
      this.listings = listings;
    })
  }
}
```

> Lihat pada console.log, begitulah cara memasang service firebase ke dalam component.

## Firebase Authentication Login dan Logout menggunakan account Google

* Buka `app.modul.ts`, tambahkan kode di bawah pada `firebaseConfig` :

Untuk menambahkan authentification pada firebase caranya menggunakan module `AuthProviders, AuthMethods`, import module di bawah : 

```
import { AngularFireModule, AuthProviders, AuthMethods } from 'angularfire2';
```

```
const firebaseAuthConfig = {
  provider: AuthProviders.Google,
  method: AuthMethods.Popup
}
```

* Tambahkan juga `firebaseAuthConfig` pada modul `app.module.ts`

```
imports: [
    AngularFireModule.initializeApp(firebaseConfig, firebaseAuthConfig),
  ],
```

* Pada class `NavComponent` buat fungsi login dan logout, yang berada pada file `nav.component.ts`

```
login(){
    this.af.auth.login();
  }
  logout(){
    this.af.auth.logout();
  }
```

* Langkah terakhir, buka `nav.component.html` tambahkan kode di bawah :
Menampilkan button signin dan signout pada navbar

```
<ul class="nav navbar-nav navbar-right">
    <li *ngIf="!(af.auth | async)"><a (click)="login()">Sign in</a></li>
    <li *ngIf="(af.auth | async)"><a (click)="logout()">Sign out</a></li>
</ul>
```

Pada class menu tambahkan kode di bawah :
- Jika posisi signin, menu `products` dan `tambah products` tidak di tampilkan.
- Saat klik tombol signin akan muncul modal login menggunakan google
- setelah login menggunkan google menu `products` dan `add-products` akan muncul.

```
 <li *ngIf="(af.auth | async)"> <a [routerLink]="['/products']">Products</a></li>
<li *ngIf="(af.auth | async)"> <a [routerLink]="['/add-product']">Tambah Product</a></li>
```

# Memanggil Halaman dengan link

* Selanjutnya kita akan memangil halaman `product` dari halaman `products`, sebelum nya buat dahulu componentnya yang di butuhkan :

```
ng g component pages/products
ng g component pages/product
ng g component pages/add-products
```

* Pada component `app.route.ts` isi dengan code di bawah :

```
    {
        path: 'products',
        component: ProductsComponent
    },
    {
        path:'product/:id', 
        component: ProductComponent
    },
    {
        path: 'add-product',
        component: AddProductComponent
    },
```

* Pada component `products.component.html` isi dengan code di bawah :

```
<div class="row">
    <div class="col-xs-4">
        <ul class="list-group">
            <li class="list-group-item" *ngFor="let product of products">
                <a [routerLink]="['/product/'+product.$key]">{{product.title}}</a>
                <a [routerLink]="['/product/'+product.$key]">{{product.city}}</a>
            </li>
        </ul>
    </div>
</div>
```

* Pada component `product` isi dengan code di bawah :

```

```

* Pada component `add-product` isi dengan code di bawah :

```

```

# Menggunakan Modeul `flash-messages`

* Pada `app.modul.ts`

```
import {FlashMessagesModule} from 'angular2-flash-messages';

=================================================================
imports: [

    FlashMessagesModule,
    RouterModule.forRoot(appRoutes),
    AngularFireModule.initializeApp(firebaseConfig, firebaseAuthConfig),
  ],
```

* Tambahkan import `FlashMessagesService` pada file `nav.component.ts` dan `homepages.component.ts`

```
import {FlashMessagesService } from 'angular2-flash-messages';
```

* Tambahkan Juga constructor `FlashMessagesService` pada file `nav.component.ts`

```
constructor(
    public af: AngularFire,
    public flashMessage: FlashMessagesService
) { }
```

* Edit fungsi `logout` pada file `nav.component.ts` menjadi seperti di bawah :

```
logout(){
    this.af.auth.logout();
    this.flashMessage.show('You Are logout',
    {cssClass: 'alert-success', timeout: 3000});
  }
```

* Buka `app.component.html` tambahkan di dalam class container

```
<flash-messages></flash-messages>
```


# Menampilkan Data product ke `product.component.html`

* Untuk menampilakan data product berdasarkan id atau key, dengan menggunakan class `FirebaseObjectObservable` yaitu di gunakan untuk menampilkan isi data/object yang ada di dalam tabel 'products' pada firebase. atau dalam database sql `menampilkan isi dalam field/object` dalam tabel.

Contoh data yang di tampilkan dengan `FirebaseObjectObservable`

```Object {
    bedrooms: 15, 
    city: "San Francisco", 
    image: "mansion1.jpg", 
    owner: "Bruce Springstien", 
    path: "/img/mansion1.jpg"…}
```

> Sedangkan

* class `FirebaseListObservable` yaitu yang di gunakan untuk menampilkan jumlah object yang tersimpan dalam tabel 'products' pada firebase, yang berbentuk array. atau dalam sql `menampilkan field/object` yang ada dalam tabel dalam bentuk array.

Contoh menampilkan array dengan `FirebaseListObservable`

```
Array[3]
0: Object
1: Object
2: Object

```

 
* Buka file `product.component.ts`

```

```











## Error

```
ive got this strange error when cli compiles: Property 'path' does not exist on type 'any[]' :

In 'firebase.services.ts' make these changes.
1. Add the following key/value to the INTERFACE for Listing:
path?: string;
2. Change declaration of CLASS property 'listing' to : 
listing: FirebaseObjectObservable<Listing>;
3. Add TypeHinting to the CLASS method addListing(listing) : 
addListing(listing: Listing)﻿

```

## Error 2: `ERROR in FlashMessagesModule is not an NgModule`

```
ERROR in FlashMessagesModule is not an NgModule
webpack: Failed to compile.
webpack: Compiling...
Hash: 8ae7ec82ee7447a3db62
Time: 5022ms
```