---
layout: post
title: Memulai Angular4 dan Firebase
categories: [angular4, firebase]
tags: [angular4, firebase]
description: Memulai Angular4 dan Firebase
---

# Memulai Angular4 dan Firebase

* Install `@angular/cli@latest` [angular/cli](https://github.com/angular/angular-cli#installation)

```
npm install -g @angular/cli@latest
```

* Buat Project menggunakan angular/cli

```
$ ng new ng4-quickstart
```

```
D:\Tools\Tutorial-Angular\ng4-quickstart>ng -v
    _                      _                 ____ _     ___
   / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
  / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
 / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
/_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
               |___/
@angular/cli: 1.0.0
node: 6.10.0
os: win32 ia32
@angular/common: 4.0.0
@angular/compiler: 4.0.0
@angular/core: 4.0.0
@angular/forms: 4.0.0
@angular/http: 4.0.0
@angular/platform-browser: 4.0.0
@angular/platform-browser-dynamic: 4.0.0
@angular/router: 4.0.0
@angular/cli: 1.0.0
@angular/compiler-cli: 4.0.0
```

* Update Paket yang di butuhkan di dalam project

```
On Windows: npm install @angular/common@next @angular/compiler@next @angular/compiler-cli@next @angular/core@next @angular/forms@next @angular/http@next @angular/platform-browser@next @angular/platform-browser-dynamic@next @angular/platform-server@next @angular/router@next @angular/animations@next --save
```

* Setelah install paket yang di butuhkan tampilan version akan seperti di bawah

```
D:\Tools\Tutorial-Angular\ng4-quickstart>ng -v
    _                      _                 ____ _     ___
   / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
  / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
 / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
/_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
               |___/
@angular/cli: 1.0.0
node: 6.10.0
os: win32 ia32
@angular/animations: 4.0.0
@angular/common: 4.0.0
@angular/compiler: 4.0.0
@angular/compiler-cli: 4.0.0
@angular/core: 4.0.0
@angular/forms: 4.0.0
@angular/http: 4.0.0
@angular/platform-browser: 4.0.0
@angular/platform-browser-dynamic: 4.0.0
@angular/platform-server: 4.0.0
@angular/router: 4.0.0
@angular/cli: 1.0.0
```

## Cara Membuat Component, Directive dan Pipe menggunakan `@angular/cli`

* Membuat `Component`

Untuk membuat component jalankan perintah di bawah di dalam project, akan terbetuk folder `hello` di dalam : `D:\ng4-quickstart\src\app`

```
$ ng g component hello
installing component
  create src\app\hello\hello.component.css
  create src\app\hello\hello.component.html
  create src\app\hello\hello.component.spec.ts
  create src\app\hello\hello.component.ts
  update src\app\app.module.ts
```

* Membuat `Directive`

Untuk membuat `directive` di dalam folder shared, jalankan perintah di bawah di dalam project

```
$ ng g directive shared/my-dir
installing directive
  create src\app\shared\my-dir.directive.spec.ts
  create src\app\shared\my-dir.directive.ts
  update src\app\app.module.ts
```

* Membuat `pipe`

Untuk membuat `pipe` di dalam folder shared, jalankan perintah di bawah 

```
ng g pipe shared/my-pipe
installing pipe
  create src\app\shared\my-pipe.pipe.spec.ts
  create src\app\shared\my-pipe.pipe.ts
  update src\app\app.module.ts
```

*Install Component yang di butuhkan

```
ng g component pages/about

```

* Install Bootstrap ke dalam folder project

```
npm install bootstrap --save
ng4-quickstart@0.0.0 D:\Tools\Tutorial-Angular\ng4-quickstart
`-- bootstrap@3.3.7
```

* Install JQuery ke dalam folder project

```
npm install jquery --save
ng4-quickstart@0.0.0 D:\Tools\Tutorial-Angular\ng4-quickstart
`-- jquery@3.2.1
```

* Untuk Menggunakan nya nya di local project, edit `.angular-cli.json`, tambahkan kode di bawah :

```
"styles": [
            "styles.css",
            "../node_modules/bootstrap/dist/css/bootstrap.min.css"
        ],
        "scripts": [
            "../node_modules/jquery/dist/jquery.min.js",
            "../node_modules/bootstrap/dist/js/bootstrap.min.js"
        ],
```

* Menggunakan Bootsrapt CDN copy paste pada `index.html`

```
<!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

<!-- Optional theme -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">

<!-- Latest compiled and minified JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>

```

* Copy juga link cdn `JQuery`

```
<script
  src="https://code.jquery.com/jquery-3.2.1.min.js"
  integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4="
  crossorigin="anonymous"></script>
```


## Install TynnyMCE

```
npm install --save tinymce
```

* Pada angular-cli.json

```
"scripts": [
  "../node_modules/tinymce/tinymce.js",
  "../node_modules/tinymce/themes/modern/theme.js",
  "../node_modules/tinymce/plugins/link/plugin.js",
  "../node_modules/tinymce/plugins/paste/plugin.js",
  "../node_modules/tinymce/plugins/table/plugin.js"
],
```

* Jalankan perintah di bawah, dalam folder project

```
ng g component TinyEditor
installing component
  create src\app\tiny-editor\tiny-editor.component.css
  create src\app\tiny-editor\tiny-editor.component.html
  create src\app\tiny-editor\tiny-editor.component.spec.ts
  create src\app\tiny-editor\tiny-editor.component.ts
  update src\app\app.module.ts
```

*Pada `tiny-editor.component.ts` ketikkan kode seperti di bawah :

```
import { Component,
  OnInit,
  AfterViewInit,
  EventEmitter,
  OnDestroy,
  Input,
  Output
} from '@angular/core';
import 'tinymce';
import 'tinymce/themes/modern';
import 'tinymce/plugins/table';
import 'tinymce/plugins/link';
import 'tinymce/plugins/advlist';
import 'tinymce/plugins/autolink';
import 'tinymce/plugins/autoresize';
import 'tinymce/plugins/autosave';

@Component({
  selector: 'app-tiny-editor',
  templateUrl: './tiny-editor.component.html',
  styleUrls: ['./tiny-editor.component.css'],
  template: `<textarea id="{{elementId}}"></textarea>`
})
export class TinyEditorComponent implements AfterViewInit, OnDestroy, OnInit {
  @Input() elementId: String;
  @Output() onEditorKeyup = new EventEmitter();
 
  constructor() {}

  ngOnInit() {
  }


  editor;
 
  ngAfterViewInit() {
    tinymce.init({
      selector: '#' + this.elementId,
      plugins: ['link', 'table'],
      skin_url: 'assets/skins/lightgray',
      setup: editor => {
        this.editor = editor;
        editor.on('keyup change', () => {
          const content = editor.getContent();
          this.onEditorKeyup.emit(content);
        });
      }
    });
  }
  ngOnDestroy() {
    tinymce.remove(this.editor);
  }
}
```

* Untuk Menampilkan tinyMCE copy kode di bawah pada `app.component.html`

```
<app-tiny-editor [elementId]="'my-editor'" (onEditorKeyup)="keyupHandler($event)">
</app-tiny-editor>
```

* Menerapkan tinyMCE pada bootstraps

```
<div class="form-group">
                    <label for="textArea" class="col-lg-2 control-label">Body</label>
                    <div class="col-lg-10">
                        <label for="post-body"></label>
                        <app-tiny-editor [elementId]="'post-body'" (onEditorKeyup)="keyupHandler($event)">
                        </app-tiny-editor>
                        <span class="help-block">A longer block of help text that breaks onto a new line and may extend beyond one line.</span>
                    </div>
                </div>
```




> Error Message Pada angular2

```
Your global Angular CLI version (1.0.0) is greater than your local
version (1.0.0-beta.32.3). The local Angular CLI version is used.

To disable this warning use "ng set --global warnings.versionMismatch=false".
```

* Jalankan perintah di bawah pada project angular anda :

```
\ng4-tutor>ng set --global warnings.versionMismatch=false
```
