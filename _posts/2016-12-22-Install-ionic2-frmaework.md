---
layout: post
title: Belajar App Mobile dengan Ionic dan Firebase
categories: [ionic, firebase]
tags: [firebase, ionic, typescript, cordova]
description: App Mobile dengan Ionic.
---


MEMBUAT APPLIKASI MOBIL DENGAN ANGULAR 2 DAN IONIC 2

- $ npm install -g cordova
- $ npm install -g ionic
- $ npm install -g typescript
- $ npm install -g typings

- Jika Gagal

	Note: If you see errors you don't understand, you may want to uninstall previous versions of ionic-cli with npm uninstall -g ionic, clear your cache with npm cache clean and then now install ionic-cli with npm install -g ionic


- $ ionic info

			******************************************************
			 Dependency warning - for the CLI to run correctly,
			 it is highly recommended to install/upgrade the following:

			 Please install your Cordova CLI to version  >=4.2.0 `npm install -g cordova`

			******************************************************

			Your system information:

			 You have been opted out of telemetry. To change this, run: cordova telemetry on
			.
			6.4.0

			Ionic CLI Version: 2.1.17
			Ionic App Lib Version: 2.1.7
			ios-deploy version: Not installed
			ios-sim version: Not installed
			OS: Windows 7
			Node Version: v6.9.1
			Xcode version: Not installed


			******************************************************

MEMBUAT PROJECT IONIC

- $ ionic start githubIonic tutorial --v2
- $ cd githubIonic
- $ ionic serve
		
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

- Buka http://localhost:8100/

##Install packages yang di butuhkan : 

- $ npm install @ionic/app-scripts@latest --save-dev 				//install @ionic/app-scripts terbaru
- $ npm install @types/request@0.0.30 --save-dev --save-exact
- $ npm install @types/jasmine@2.5.36 --save-dev --save-exact       //install dependency firebase
- $ npm install firebase angularfire2 --save

