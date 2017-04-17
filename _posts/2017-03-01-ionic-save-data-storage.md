---
layout: post
title: ionic save data storage
categories: [ionic2, angular2]
tags: [angular2, ionic2]
description: Hosting firebase.
---
> STEP 1

```
ionic start save-data --v2
```

> STEP 2

```
cordova plugin add cordova-sqlite-storage --save
```
Fetching plugin "cordova-sqlite-storage@2.0.2" via npm
Saved plugin info for "cordova-sqlite-storage" to config.xml

> STEP 3

```
npm install --save @ionic/storage
```

`home.ts`

```
  setData(){
    this.storage.set('myData','hello');
  }

  getData(){
    this.storage.get('myData').then((data) => {
      console.log(data);
    });
  }
```

