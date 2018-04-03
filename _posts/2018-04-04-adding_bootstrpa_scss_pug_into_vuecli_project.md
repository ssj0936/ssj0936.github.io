---
layout: post
title: "VUE-CLI下加入bootstrap4 + SCSS + PUG"
subtitle: "手把手教你怎麼在vue-cli專案下寫bootstrap SCSS 和 pug"
date: 2018-04-04
author: "Timothy"
tags: vue-cli bootstrap scss pug
---
* * *

之前的project時有用過bootstrap3，後來看到了bootstrap4的消息，研究了一下發現從3到4這一步真的是大躍進！對我最直接的影響大概是grid系統大翻新改用flexbox，classname中的col也不用再填數字了，大小單位從px改用rem更有彈性，真的很棒！

這裡記錄一下在vue-cli中加入bootstrap4 + SCSS + PUG的步驟

* * *

## VUE-CLI

先npm安裝：
```
$ npm install vue-cli -g
```
接著initial一個新的project，並進到其目錄中
```
$ vue init webpack [project-name]
$ cd [project-name]
```
* * *
## PUG相關
**PUG**是HTML的模板語言，不用start/end tag

用的是縮排來做階層表示，省去你寫一堆tag的時間




先npm安裝
```
$ npm install pug pug-loader pug-filters --save
```
然後在`webpack.base.conf.js` 裡面的module加入
```
{
  test: /\.pug$/, 
  loader: 'pug'
}
```
(但我發現好像只需要安裝就好了，加入module這步好像不需要做也會work)

* * *
## SCSS

裝**SCSS**主要是想要在CSS裡面用變數


先npm安裝
```
$ npm install sass sass-loader node-sass --save
```
然後在`webpack.base.conf.js` 裡面的module加入
```
{
  test: /\.scss$/,
  loader: 'style!css!sass?sourceMap'
}
```
(但我發現這好像也只需要安裝就好了，加入module這步好像不需要做也會work)

* * *
## BootStrap

**bootstrap**中會需要**popper**和**jquery**

一樣npm安裝
```
$ npm install bootstrap --save
$ npm install jquery --save 
$ npm install popper.js --save 
```

並在`webpack.base.conf.js` 做一點修改：

```js
// 檔案開頭先把webpack require進來
const webpack = require('webpack')
...
..
.
plugins: [
  new webpack.ProvidePlugin({
    '$': "jquery",
    'jQuery': "jquery",
    'Popper': 'popper.js'
  })
],
...
```
最後在專案裡面的main.js裡面把bootstrap import進來

```
import 'bootstrap';
import 'bootstrap/dist/css/bootstrap.css';
```

* * *
## DONE!!

完成惹，是不是很簡單呢？
想要試看看能不能work，可以把下面的code置換完全覆蓋到HelloWorld.vue
<script src="https://gist.github.com/ssj0936/e5fc2b8b1f8f63df685d9cc73d4a9cb7.js"></script>
然後在command line輸入
```
$ npm run dev
```
接著去`http://localhost:8080/`看看成果

