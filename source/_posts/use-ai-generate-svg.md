---
title: 学会使用ai作图
date: 2025-05-14 21:49:30
tags: ai技巧
author: whopxx
email: 2074447320@qq.com
---
## SVG

即可缩放矢量图形（Scalable Vector Graphics），是一种基于可扩展标记语言（XML）的矢量图形格式。用代码描述矢量图形，你可以把它理解成“用文字画图”。和常见的JPG、PNG等位图完全不同，天生为网页而生，可玩性更高一些。
```html
<svg width="200" height="100" xmlns="http://www.w3.org/2000/svg">
  <rect x="50" y="20" width="100" height="60" fill="red" />
</svg>
```
对于一个svg的样式，可以内嵌html显示或者用浏览器直接打开编辑好的.svg文件，所以这里让ai直接生成完整的svg代码来实现用户良好的图像。

## AI prompt
```
根据要求绘制各种图片，如流程图等
以SVG形式给出
你的绘图遵循以下原则
1. 尽量美观，配色简洁舒适
2. 保证局部的对称和居中，尤其是箭头以及箭头上的文字
3. 不要使用曲线
你的背景可以参考这个：
<!-- 渐变背景 -->
<defs>
<linearGradient id="bgGradient" x1="0%" y1="0%" x2="100%" y2="100%">
<stop offset="0%" style="stop-color:#f8f9fa;stop-opacity:1" />
<stop offset="100%" style="stop-color:#e9ecef;stop-opacity:1" />
</linearGradient>
<linearGradient id="stackGradient" x1="0%" y1="0%" x2="0%" y2="100%">
<stop offset="0%" style="stop-color:#e9f2ff;stop-opacity:1" />
<stop offset="100%" style="stop-color:#d7e5f5;stop-opacity:1" />
</linearGradient>
<filter id="shadow" x="-10%" y="-10%" width="120%" height="120%">
<feDropShadow dx="3" dy="3" stdDeviation="3" flood-opacity="0.2"/>
</filter>
<!-- 定义箭头 -->
<marker id="arrowhead" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
<polygon points="0 0, 10 3.5, 0 7" fill="#495057" />
</marker>
</defs>
```
## 示例
1. 任务
```
我需要了解mysql主从复制架构完整流程，需要有详细的文字介绍

根据要求绘制各种图片，如流程图等
以SVG形式给出
你的绘图遵循以下原则
1. 尽量美观，配色简洁舒适
2. 保证局部的对称和居中，尤其是箭头以及箭头上的文字
3.不要使用曲线
你的背景可以参考这个：
<!-- 渐变背景 -->
<defs>
<linearGradient id="bgGradient" x1="0%" y1="0%" x2="100%" y2="100%">
<stop offset="0%" style="stop-color:#f8f9fa;stop-opacity:1" />
<stop offset="100%" style="stop-color:#e9ecef;stop-opacity:1" />
</linearGradient>
<linearGradient id="stackGradient" x1="0%" y1="0%" x2="0%" y2="100%">
<stop offset="0%" style="stop-color:#e9f2ff;stop-opacity:1" />
<stop offset="100%" style="stop-color:#d7e5f5;stop-opacity:1" />
</linearGradient>
<filter id="shadow" x="-10%" y="-10%" width="120%" height="120%">
<feDropShadow dx="3" dy="3" stdDeviation="3" flood-opacity="0.2"/>
</filter>
<!-- 定义箭头 -->
<marker id="arrowhead" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
<polygon points="0 0, 10 3.5, 0 7" fill="#495057" />
</marker>
</defs>
```
2. 根据ai生成的svg代码进行预览
这里可以用一些在线的svg解析网站或者自己保存为svg文件预览。
生成代码如下：
```html
<svg width="800" height="600" viewBox="0 0 800 600" xmlns="http://www.w3.org/2000/svg">
  <!-- 引用用户提供的渐变和箭头定义 -->
  <defs>
    <linearGradient id="bgGradient" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#f8f9fa;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#e9ecef;stop-opacity:1" />
    </linearGradient>
    <marker id="arrowhead" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
      <polygon points="0 0, 10 3.5, 0 7" fill="#495057" />
    </marker>
  </defs>

  <!-- 背景 -->
  <rect width="100%" height="100%" fill="url(#bgGradient)" />

  <!-- 主库组件 -->
  <g transform="translate(100, 150)">
    <rect x="0" y="0" width="200" height="300" rx="10" fill="#fff" filter="url(#shadow)" />
    <text x="100" y="30" text-anchor="middle" font-size="16" fill="#2d3436">Master</text>
    <rect x="20" y="60" width="160" height="40" fill="#e9f2ff" rx="5" />
    <text x="100" y="85" text-anchor="middle" font-size="14">Binlog</text>
    <rect x="20" y="120" width="160" height="40" fill="#d7e5f5" rx="5" />
    <text x="100" y="145" text-anchor="middle" font-size="14">Binlog Dump线程</text>
  </g>

  <!-- 从库组件 -->
  <g transform="translate(500, 150)">
    <rect x="0" y="0" width="200" height="300" rx="10" fill="#fff" filter="url(#shadow)" />
    <text x="100" y="30" text-anchor="middle" font-size="16" fill="#2d3436">Slave</text>
    <rect x="20" y="60" width="160" height="40" fill="#e9f2ff" rx="5" />
    <text x="100" y="85" text-anchor="middle" font-size="14">Relay Log</text>
    <rect x="20" y="120" width="160" height="40" fill="#d7e5f5" rx="5" />
    <text x="100" y="145" text-anchor="middle" font-size="14">I/O线程</text>
    <rect x="20" y="180" width="160" height="40" fill="#d7e5f5" rx="5" />
    <text x="100" y="205" text-anchor="middle" font-size="14">SQL线程</text>
  </g>

  <!-- 箭头与流程标签 -->
  <path d="M300 200 L500 200" stroke="#495057" stroke-width="2" marker-end="url(#arrowhead)" />
  <text x="400" y="190" text-anchor="middle" font-size="12" fill="#495057">Binlog事件传输</text>
  <path d="M300 250 L500 250" stroke="#495057" stroke-width="2" marker-end="url(#arrowhead)" />
  <text x="400" y="240" text-anchor="middle" font-size="12" fill="#495057">ACK确认（半同步）</text>
</svg>
```
3. 示例图片如下
![](https://github.com/whopxxx/whopxx/blob/main/picture_resources/bolg/ai_g_svg_t_2025_5_14.png?raw=true)