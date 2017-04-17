---
layout: post
title: Memulai Angular-material dan Firebase
categories: [material, firebase]
tags: [material, firebase]
description: Memulai Angular material dan Firebase
---

# Belajar Angular Material dan Firebase
[material-angular](https://material.angular.io/)

```
ng new fireMaterial

cd fireMaterial
```

* Install Material dalam folder project*
```
npm install --save @angular/material
```

* Install Angular Animation*

```
npm install --save @angular/animations
```

Pada `app.module.ts`, import code di bawah:

```
import {BrowserAnimationsModule} from '@angular/platform-browser/animations';
import { MaterialModule, MdButtonModule, MdCheckboxModule} from '@angular/material';
```

dan

```
  imports: [
    MaterialModule,
    BrowserAnimationsModule,
    MdButtonModule,
    MdCheckboxModule
  ],
```

* Theme material, Buka `index.html` pada root folder copy code di bawah : *

```
<link href="../node_modules/@angular/material/prebuilt-themes/indigo-pink.css" rel="stylesheet">
```

* Icon Material, Buka `index.html` pada root folder copy code di bawah : *

```
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
```

* Gesture: tambahkan `hammerJs` ke dalam folder project, jika kita akan 
menggunakan beberapa components seperti (md-slide-toggle, md-slider, mdTooltip) menggunakan HammerJS untuk gestures.*

```
npm install --save hammerjs
```

After installing, import pada app's root module.

```
import 'hammerjs';
```

* Buka file `.angular-cli.json`, edit bagian di bawah :

```
"styles": [
        "styles.css"
      ],
```

> Menjadi 

```
"styles": [
        "styles.scss"
      ],
```

```
"defaults": {
    "styleExt": "css",
    "component": {}
  }
```

> Menjadi 

```
"defaults": {
    "styleExt": "scss",
    "component": {}
  }
```

* Define SCSS, jika kita meggunakan scss buat file `style.scss` dan copy kode di bawah(haspus terlebih daulu file style.css):*

```
@import '~@angular/material/theming';
// Plus imports for other components in your app.

// Include the base styles for Angular Material core. We include this here so that you only
// have to load a single css file for Angular Material in your app.
@include mat-core();

// Define the palettes for your theme using the Material Design palettes available in palette.scss
// (imported above). For each palette, you can optionally specify a default, lighter, and darker
// hue.
$candy-app-primary: mat-palette($mat-indigo);
$candy-app-accent:  mat-palette($mat-pink, A200, A100, A400);

// The warn palette is optional (defaults to red).
$candy-app-warn:    mat-palette($mat-red);

// Create the theme object (a Sass map containing all of the palettes).
$candy-app-theme: mat-light-theme($candy-app-primary, $candy-app-accent, $candy-app-warn);

// Include theme styles for core and each component used in your app.
// Alternatively, you can import and @include the theme mixins for each component
// that you are using.
.app-primary{
@include angular-material-theme($candy-app-theme);
}

```


* buka file `app.component.html` copy code di bawah :*

```
<md-sidenav-container class="app-primary">

    <md-sidenav #sidenav mode="side" class="app-sidenav">
        Sidenav
    </md-sidenav>

    <md-toolbar color="primary">
        <button class="app-icon-button" (click)="sidenav.toggle()">
      <i class="material-icons app-toolbar-menu">menu</i>
    </button> Angular Material2 Example App

        <span class="app-toolbar-filler"></span>
        <button md-button (click)="isDarkTheme = !isDarkTheme">TOGGLE DARK THEME</button>
    </md-toolbar>

    <div class="app-content">
        Ini adalah Contetnt
    </div>

</md-sidenav-container>
<span class="app-action" [class.m2app-dark]="isDarkTheme">
  <button md-fab><md-icon>check circle</md-icon></button>
</span>
```

* Untuk merubah warna buka file style.scss dan copy kode di bawah:*

```
$candy-app-primary: mat-palette($mat-light-green);
$candy-app-accent: mat-palette($mat-light-green, A200, A100, A400);
```

* Contoh Script Google Analytic:*

```
<body>
  <material2-app-app>Loading...</material2-app-app>

  <script>
    (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
    (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
    m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
    })(window,document,'script','//www.google-analytics.com/analytics.js','ga');
    ga('create', 'number', 'auto');
    ga('send', 'pageview');
  </script>
</body>
```

* Install ANgularFire2 ke dalam folder project *

```
npm install firebase angularfire2 --save
```