# CSS时钟
# 需求：一个时钟

### 分析需求
* 一个圆，有刻度最好
* 三个指针：时分秒，不同粗细，不同长短，
* 时分秒指针会按不同的时间频率转动

<img src="http://demo.hmmix.com/clock/clock.png" width="50%">

### 第一步 实现圆
```
一个DIV边线加上圆的属性
定宽，度，边线，设圆的属性
border-radius
```

###  第步二 实现时分秒指针
```
用div或者用伪元素都可以。
background-image: linear-gradient(to bottom, red 0%,red 50%, rgba(255,255,255,0) 51%,rgba(255,255,255,0) 100%);
不能用left 50%,因为旋转是整体
```

### 第三步 实现转动
```
animation:jishi 60*60s steps(60) infinite;
动画名  执行时间  执行步数  执行次数
transform: rotate(0-360deg)
```
60s 60*60s 60*60s*12 时分秒的一圈执行时间，时间是12

### 改进一  增加时刻表
简单的方法，用一个图，问题不好自适应大小
所以用了svg  所以确点没有那么好看，好处可以自适应

### 改进二  增加文字显示的同步计时
~~~
用的电子字体，一行两个字，平移高度来切换显示文字高度
~~~

### 改进三  用div的attr设定每个指针从当前时间开始
~~~
animationDelay：延时执行，如果是负数，则反过来，提前跑到哪个位置
--number 传参
单位不能直接拼接，需要calc计算
animation-delay:calc(var(--number) * -60s);
~~~

------------
总结用到的关键属性:
##### linear-gradient
##### animation
##### animation-delay
##### --css变量
##### 需要改变属性切换的时候，用css传参实现，改一个值适配
------------


