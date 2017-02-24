Rythm.js 中文
========

[![Build Status](https://travis-ci.org/Okazari/Rythm.js.svg?branch=master)](https://travis-ci.org/Okazari/Rythm.js)
[![Code Climate](https://codeclimate.com/github/Okazari/Rythm.js/badges/gpa.svg)](https://codeclimate.com/github/Okazari/Rythm.js/code)

示例位于 : https://okazari.github.io/Rythm.js/

一个使你的页面跳舞的JavaScript 库

当前处于开发阶段

入门
===============

使用npm 安装

```
npm install rythm.js
```

CDN: https://unpkg.com/rythm.js/

好的老办法
------------

在你的页面引入 rythm。

```html
<script type="text/javascript" src="/path/to/rythm.js"></script>
```

在元素中引入rythm css 类中的一个指示其将会跳舞。

```html
<div class="rythm-bass"></div>
```

创建一个Rythm 对象，并且传入你的音频url 地址，然后调用start 方法。
```javascript
var rythm = new Rythm();
rythm.setMusic("path/to/sample.mp3");
rythm.start();
```

ES6 模块
----------

```js
import Rythm from 'rythm.js'
const rythm = new Rythm();
rythm.setMusic("path/to/sample.mp3");
rythm.start();
```

文档
=============

Rythm 对象
------------

```javascript
var rythm = new Rythm();

/* startingScale 是你的元素接受的最小的缩放值 (缩放比率是 startingScale + (pulseRatio * currentPulse));
 * Value 取值范围在 0-1
 * 默认值为 0.75
 */
rythm.startingScale = value;

/* pulseRatio is 是你的元素接受的最大的缩放值 (缩放比例是 startingScale + (pulseRatio * currentPulse))
 * Value 取值范围在 0-1
 * Default 0.50
 */
rythm.pulseRatio = value;

/* maxValueHistory代表传入的会被存储起来去计算currentPulse的数值的数量
 * 整数类型 value, 最小值 1
 * 默认值为 100
 */
rythm.maxValueHistory = value;

/* 设置页面将要跳的音乐.
 * @audioUrl : '../example/mysong.mp3'
 */
rythm.setMusic(audioUrl);

/* 用于同其他的播放器库协作
 * 你可以连接 Rythm 到一个 audioElement, 然后使用你的其他播放器去控制audio。
 */
rythm.connectExternalAudioElement(audioElement)

/* 调整音乐的音量。
 * @value : Number
 */
rythm.setGain(value);

/* 添加你自己的 rythm-class
 * @elementClass: Class 你想要链接你的 rythm 。
 * @danceType : Atm just use "size";
 * @startValue: 你的rythm 开始的频率。
 * @nbValue: 你的rythm 频率的值。
 * 1024 Frequences, 你的 rythm 将会响应你选择的频率的平均值。
 * Exemples : bass 0-10 ; medium 150-40 ; high 500-100
 */
rythm.addRythm(elementClass, danceType, startValue, nbValue);

/* 安装你的电脑麦克风到 rythm.js
 * 函数返回一个promise 解析，当麦克风可用。
 * 要求你的网站是 HTTPS
 */
rythm.plugMicrophone().then(function(){...})

//开始跳舞
rythm.start();

//停止
rythm.stop();
```

类
-------

+ rythm-bass
+ rythm-medium
+ rythm-high

自定义类
--------------

你可以使用 `addRythm` 方法让你自己的类去监听特定的频率。
这是基础类是如被创建的的：
+ `addRythm('rythm-bass','size',0,10);`
+ `addRythm('rythm-medium','size',150,40);`
+ `addRythm('rythm-high','size',500,100);`

特征
========

 + 你真的可以添加类使你的HTML 元素跟随你的音乐节奏跳动。

未来
------
 + 添加更多的 rythm class 频率
 + 添加 rythm 移动类型 (心跳、旋转等等...)

贡献
==========

感谢任何PR. 你可以按照下面步骤开始：
 + Fork 这个项目
 + Clone 你的仓库
 + 运行 ```npm install```
 + 运行 ```nom start``` 在主文件夹中去启动一个开发web 服务器。
 + Enjoy the rythm.
