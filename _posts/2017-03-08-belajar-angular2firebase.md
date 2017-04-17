---
layout: post
title: Belajar Angular2 dan Firebase
categories: [angular2, firebase]
tags: [angular2, firebase]
description: Belajar Angular2 dan Firebase
---

```
$ ng new angular2firebase
```

* Tambahkan library firebase dalam folder project

```
$ npm install firebase --save

angular2firebase@0.0.0 D:\Tools\Tutorial-Angular\angular2firebase
`-- firebase@3.7.0
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

```

## Config Firebase
> Buat dan buka file `angular2firebase\src\environments\firebase.config.ts` dan edit menjadi seperti di bawah

```
// Initialize Firebase
  export const firebaseConfig = {
    apiKey: "AIzaSyBn6S1YkBriVWp7wR5ytPOQXbI06F7pQ5A",
    authDomain: "angular2firebase-559ee.firebaseapp.com",
    databaseURL: "https://angular2firebase-559ee.firebaseio.com",
    storageBucket: "angular2firebase-559ee.appspot.com",
    messagingSenderId: "272606209095"
  };
```

* Tambahkan angularfire2 library ke dalam folder project

```
$ npm install angularfire2 --save
```

* Pada app.modul.ts tambahkan import di bawah :

```
import { firebaseConfig } from '../environments/firebase.config';
import { AngularFireModule } from 'angularfire2';
```

* Pada baris `imports` tambahkan menjadi seperti di bawah :

```
imports: [
    BrowserModule,
    FormsModule,
    HttpModule,
    AngularFireModule.initializeApp(firebaseConfig)
  ],
```

* Pada `app.component.ts` edit menjadi seperti di bawah :
 
```
import { Component } from '@angular/core';
import { initializeApp, database } from 'firebase';
import { firebaseConfig } from '../environments/firebase.config';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'app works!';

  constructor(){
    
  initializeApp(firebaseConfig);

  var root = database().ref();

  root.on('value', function(snap){
    console.log(snap.val());
  });
  }
}
```

* Install angularfire2 library

```
$ npm install angularfire2 --save
```

## Membuat Component Home

```
$ ng generate component home
installing component
  create src\app\home\home.component.css
  create src\app\home\home.component.html
  create src\app\home\home.component.spec.ts
  create src\app\home\home.component.ts
  update src\app\app.module.ts
```
