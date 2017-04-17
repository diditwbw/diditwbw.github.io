---
layout: post
title: Memulai App Mobile dengan Ionic dan Firebase
categories: [ionic, firebase]
tags: [firebase, ionic]
description: Applikasi Mobile dengan Ionic dan Firebase.
---

## Memasang AndroidSDK

Download: | 
[AndroidSdk](https://dl.google.com/android/repository/tools_r25.2.3-windows.zip) |
[apache ant](http://mirror.wanxp.id/apache//ant/binaries/apache-ant-1.9.7-bin.zip) |
 
## Pasang Path di windows

{% highlight yaml %}
Variabel Name: ANDROID_HOME 
Variabel Value: D:\Tools\android_sdk\tools;D:\Tools\android_sdk\platform-tools
{% endhighlight %}

## Jalankan di command promp :

{% highlight yaml %}
set ANDROID_HOME=D:\Tools\android_sdk
set PATH=%PATH%;%ANDROID_HOME%\tools;%ANDROID_HOME%\platform-tools
{% endhighlight %}

Download versi/API Android dari yang bawah sampai dengan yang tertinggi.

{% highlight yaml %}
4.0(API 14) dan 7.1(API 25)
{% endhighlight %}

## STEP 2

> Install yang di butuhkan :

{% highlight yaml %}
$ npm install -g cordova
$ npm install -g ionic
$ npm install -g typescript
$ npm install -g typings
{% endhighlight %}

## clear cache instalasi

{% highlight yaml %}
$ npm cache clean
{% endhighlight %}

> Jika Error / Gagal

Note: If you see errors you don't understand, you may want to uninstall previous versions of ionic-cli with npm uninstall -g ionic, clear your cache with npm cache clean and then now install ionic-cli with npm install -g ionic

{% highlight yaml %}
$ ionic info

******************************************************
Dependency warning - for the CLI to run correctly,
it is highly recommended to install/upgrade the following:

Please install your Cordova CLI to version  >=4.2.0 `npm install -g cordova`

******************************************************

Your system information:

You have been opted out of telemetry. To change this, run: cordova telemetry on

6.4.0

Ionic CLI Version: 2.1.17
Ionic App Lib Version: 2.1.7
ios-deploy version: Not installed
ios-sim version: Not installed
OS: Windows 7
Node Version: v6.9.1
Xcode version: Not installed

{% endhighlight %}

## Membuat Project ionic dan firebase

`ionic start` untuk membuat applikasi.
`debtTracker` nama dari applikasi yang di buat.
`blank` memulai Ionic CLI dengan blank template
`--v2` tells the Ionic CLI you want to create an Ionic 2 project instead of an Ionic 1 project.

{% highlight yaml %}
$ ionic start contohIonic blank --v2
$ cd contohIonic
$ ionic serve
		
[15:45:51]  ionic-app-scripts 0.0.47
[15:46:07]  watch started ...
[15:46:07]  build dev started ...
[15:46:07]  clean started ...
[15:46:07]  clean finished in 2 ms
[15:46:07]  copy started ...
[15:46:07]  transpile started ...
[15:46:35]  transpile finished in 28.07 s
[15:46:35]  webpack started ...
[15:46:38]  copy finished in 31.22 s
[15:47:03]  webpack finished in 27.71 s
[15:47:03]  sass started ...
[15:47:09]  sass finished in 5.99 s
[15:47:09]  build dev finished in 61.98 s
[15:47:11]  watch ready in 63.99 s
[15:47:11]  dev server running: http://localhost:8100/
{% endhighlight %}

- Buka http://localhost:8100/

## Install packages yang di butuhkan : 

{% highlight yaml %}
//install @ionic/app-scripts terbaru
$ npm install @ionic/app-scripts@latest --save-dev 	
$ npm install @types/request@0.0.30 --save-dev --save-exact
//install dependency firebase
$ npm install @types/jasmine@2.5.36 --save-dev --save-exact
$ npm install firebase angularfire2 --save
{% endhighlight %}

## IMPORT 

{% highlight yaml %}
$ ionic generate page EventDetail
$ ionic generate page EventCreate
$ ionic generate page EventList
$ ionic generate page Login
$ ionic generate page Profile
$ ionic generate page ResetPassword
$ ionic generate page Signup
{% endhighlight %}

{% highlight yaml %}
$ ionic generate provider EventData
$ ionic generate provider AuthData
$ ionic generate provider ProfileData
{% endhighlight %}

## Buka `app.module.ts` edit seperti di bawah

{% highlight yaml %}
import { NgModule, ErrorHandler } from '@angular/core';
import { IonicApp, IonicModule, IonicErrorHandler } from 'ionic-angular';
import { MyApp } from './app.component';

// Import pages
import { HomePage } from '../pages/home/home';
import { EventCreatePage } from '../pages/event-create/event-create';
import { EventDetailPage } from '../pages/event-detail/event-detail';
import { EventListPage } from '../pages/event-list/event-list';
import { LoginPage } from '../pages/login/login';
import { ProfilePage } from '../pages/profile/profile';
import { ResetPasswordPage } from '../pages/reset-password/reset-password';
import { SignupPage } from '../pages/signup/signup';

// Import providers
import { AuthData } from '../providers/auth-data';
import { EventData } from '../providers/event-data';
import { ProfileData } from '../providers/profile-data';
{% endhighlight %}

## initialize pada `@NgModule`:

{% highlight yaml %}
@NgModule({
    declarations: [
        MyApp,
        HomePage,
        EventCreatePage,
        EventDetailPage,
        EventListPage,
        LoginPage,
        ProfilePage,
        ResetPasswordPage,
        SignupPage
    ],
    imports: [
        IonicModule.forRoot(MyApp)
    ],
    bootstrap: [IonicApp],
    entryComponents: [
        MyApp,
        HomePage,
        EventCreatePage,
        EventDetailPage,
        EventListPage,
        LoginPage,
        ProfilePage,
        ResetPasswordPage,
        SignupPage
    ],
    providers: [
        {provide: ErrorHandler, useClass: IonicErrorHandler},
        AuthData,
        EventData,
        ProfileData
    ]
})
export class AppModule {}
{% endhighlight %}

## Untuk kode Lengkapnya:

{% highlight yaml %}
import { NgModule, ErrorHandler } from '@angular/core';
import { IonicApp, IonicModule, IonicErrorHandler } from 'ionic-angular';
import { MyApp } from './app.component';

// Import pages
import { HomePage } from '../pages/home/home';
import { EventCreatePage } from '../pages/event-create/event-create';
import { EventDetailPage } from '../pages/event-detail/event-detail';
import { EventListPage } from '../pages/event-list/event-list';
import { LoginPage } from '../pages/login/login';
import { ProfilePage } from '../pages/profile/profile';
import { ResetPasswordPage } from '../pages/reset-password/reset-password';
import { SignupPage } from '../pages/signup/signup';

// Import providers
import { AuthData } from '../providers/auth-data';
import { EventData } from '../providers/event-data';
import { ProfileData } from '../providers/profile-data';

@NgModule({
    declarations: [
        MyApp,
        HomePage,
        EventCreatePage,
        EventDetailPage,
        EventListPage,
        LoginPage,
        ProfilePage,
        ResetPasswordPage,
        SignupPage
    ],
    imports: [
        IonicModule.forRoot(MyApp)
    ],
    bootstrap: [IonicApp],
    entryComponents: [
        MyApp,
        HomePage,
        EventCreatePage,
        EventDetailPage,
        EventListPage,
        LoginPage,
        ProfilePage,
        ResetPasswordPage,
        SignupPage
    ],
    providers: [
        {provide: ErrorHandler, useClass: IonicErrorHandler},
        AuthData,
        EventData,
        ProfileData
    ]
})
export class AppModule {}
{% endhighlight %}

## Install the cordova plugins you’ll use
    
For that you’ll need to install the camera plugin from ionic-native.

{% highlight yaml %}
$ ionic plugin add cordova-plugin-camera
$ ionic serve
{% endhighlight %}

> Referensi : |
[Ionic start](https://javebratt.com/ionic-2-firebase-3-week-1/) |
