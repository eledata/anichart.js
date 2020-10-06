<h1 align="center">
anichart.js
</h1>

<p align="center">
    <img src="https://data.jsdelivr.com/v1/package/npm/anichart/badge">
    <img alt="NPM" src="https://img.shields.io/npm/l/anichart?style=flat-square">
    <img alt="npm" src="https://img.shields.io/npm/v/anichart?style=flat-square">
    <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/Jannchie/anichart.js?style=flat-square">
</p>

轻松地制作数据可视化动画视频。

## 示例

<p align="center">
    <img src="https://github.com/Jannchie/anichart.js/blob/master/public/image/anichart.js.png?raw=true"><br/>
</p>

## 写在前面

本项目开源、自由、免费。

目前正在开发中，虽然该有的功能已经实现了，但是没有提供友好的接口，想要做出自己的作品需要阅读源代码并了解JavaScript编程。

目前后端导出视频内置FFmpeg。能够直接导出MP4。

前端直接导出视频只支持webp格式。并且由于浏览器限制（也可能是自身技术限制）导出视频时需要在内存中载入整个Blob，如果直出较高帧率且时长较长的视频，很可能会爆内存（1分钟60帧的视频约需要2GB内存），因此目前只能分割导出。期待各位大佬提交PR。

如果你不满意上述操作，你也可以尝试脱离浏览器环境，在node.js环境下导出png序列，然后再整合成任意格式的视频。这个项目支持浏览器和node.js两种环境。但是还有很多坑没有解决，并且没有实现自动化。

人机交互友好的网站建设已经在搞了（指建好了仓库），还要较长一段时间才能完成。

本项目需要各位技术人员的技术支持。但如果你只是一个普通的使用者，也能通过赞助的方式支持。你可以通过[爱赞助](https://azz.net/jannchie)利用支付宝或者微信进行支持。也能通过GitHub Sponsor功能支持（需要信用卡一张）。

## 简介

这是一个更好的可视化模板。

相较于它的[前身](https://github.com/Jannchie/Historical-ranking-data-visualization-based-on-d3.js)，主要优势在于：

- 双端制作: 整合了前端和后端的优势。前端（浏览器端）可以便利地进行浏览和调试，后端（服务器端）结合FFmpeg， 可以导出高质量的视频。
- 可编程化：开放接口，允许插入自定义的代码，利用框架计算的数据，基于Canvas Api进行绘图。
- 直出视频：可以直接通过每一帧的图像渲染视频，无需借助任何录屏工具。
- 自动边距：不用再自己指定内边距，导致文字超出范围了。
- 任意比例：能够导出任何分辨率而无需后期处理。
- 高效绘图：采用Canvas而不是Svg，更加节能。
- 帧率可控：逐帧绘图，导出视频而不会掉帧。
- 逐帧调试：提供组件进行逐帧调试和播放。
- 自带插值：提供了更加友好的数据预处理。
- 优化着色：提供了更好的颜色随机算法。

此外，对于柱状图：

- 交换算法：现在的交换不必在关键帧之间卡点了。
- 显示效果：画风变了。

## 安装

### 使用Yarn

```bash
yarn add anichart
```

### 使用Npm

```bash
npm i anichart
```

### 标签导入

```html
<script src="https://cdn.jsdelivr.net/npm/anichart@1.0.6/dist/anichart.min.js"></script>
```

## 用法

### 使用Npm或者Yarn导入

如果使用标签导入可以跳过这一步，如果使用npm或者Yarn需要通过以下代码引入包：

``` js
const anichart require("anichart");
```

或者

``` js
import * as anichart from "anichart";
```

### 准备数据

以CSV文件为例。

``` csv
name,date,value,channel,other
Jannchie,2020-01-01,1,科技,other
Jannchie,2020-01-03,6,科技,other
Jannchie,2020-01-05,3,科技,other
Jannchie,2020-01-07,-,科技,other
Jannchie,2020-01-09,7,科技,other
Jannchie,2020-01-12,12,科技,other
Cake47,2020-01-03,10,生活,other
Cake47,2020-01-02,5,生活,other
Cake47,2020-01-06,2,生活,other
Cake47,2020-01-09,3,生活,other
Cake47,2020-01-11,4,生活,other
```

### 创建对象

```js
let a = new anichart.Bar();
```

### 载入数据

```js
await a.loadCsv(pathData);
a.initCanvas();
a.readyToDraw();

```

### 播放动画

```js
a.play();
```

### 测试

```bash
node --experimental-wasm-threads --experimental-wasm-bulk-memory ./test/fans-month.js
```

### 待完成事项

- [x] 自定义Bar上文字
- [x] 自定义标题
- [ ] 导入配置
- [ ] 模块化
- [ ] 建站
