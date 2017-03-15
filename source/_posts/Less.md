title: Less
date: 2017-3-11 11:41:41
description: Less基础操作
categories:
- HTML
tags:
- Less
---
# 初识less
#### 编译工具
koala

.less -> .css

#### 输出方式

normal:普通css

compress:压缩过的css

#### 注释
```
/*我会被编译的*/
    
//我不会被编译
```

# 变量
```
// @变量名：值;
@test_width:300px;

// 使用
.body{
    width: @test_width;
    height: @test_width;
}
```

# 混合

#### 纯class混合
```
=====less=====

.box{
    .border;
}

.border{
    border:solid 5px pink;
}
```
```
=====css=====

.box{
    border:solid 5px pnik;
}
```
#### 带参数混合
```
=====less=====

.border_02(@border_width){
    border:solid yellow @border_width;
}

.test_hunhe{
    .border_02(30px);
}
```
```
=====css=====

.test_hunhe {
  border: solid yellow 30px;
}
```
#### 不带参数混合(使用默认参数)
```
=====less=====

.border_radius(@radius:5px){
    -webkit-border-radius: @radius;
    -moz-border-radius: @radius;
    border-radius: @radius;
}

.radius_test{
    .border_radius(10px);
}
```
```
=====css=====

.radius_test{
    -webkit-border-radius: 10px;
    -moz-border-radius: 10pxx;
    border-radius: 10px;
}
```
# 匹配模式
```
=====less=====

.pos(r){
    position: relative;
}
.pos(a){
    position: absolute;
}
.pos(f){
    position: fixed;
}

.pipei{
    .pos(r);
}
.pipei2{
    .pos(a);
}
.pipei3{
    .pos(f);
}
```
```
=====css=====

.pipei{
    position: relative;
}
.pipei2{
    position: absolute;
}
.pipei3{
    position: fixed;
}
```
# 运算
```
=====less=====

@test_01:300px;

.box_02{
    width: (@test_01 - 20) * 5;
    color: #ccc - 10;   
    // 颜色转化成255,255,255计算
}
```
```
=====css=====

.box_02 {
  width: 1400px;
  color: #c2c2c2; 
}
```
# 嵌套
```
=====less=====

.list{
    width: 600px;
    height: 600px
    
    li{
        height: 30px;
        height: 30px;
        
        a{
            float: left;
            // &代表他的上一层选择器
            &:hover{
                color: red;
            }
            
        }
    }
}
```
```
=====css=====

.list {
  width: 600px;
  height: 600px;
}
.list li {
  height: 30px;
}
.list li a {
  float: left;
}
.list li a:hover {
  color: red;
}
```
# arguments
包含了所有传进来的参数
```
=====less=====

.border_arg(@w:30px,@c:red,@xx:solid){
    border: @arguments;
}

.test_arg{
    .border_arg(40px);
}
```
```
=====css=====

.test_arg {
  border: 40px red solid;
}
```
# 避免编译
```
=====less=====

.test_03{
    width: ~'calc(300px-30)';
}
```
```
=====css=====

.test_03 {
  width: calc(300px-30);
}
```
# !important关键字
```
=====less=====

.border_radius(@radius:5px){
    -webkit-border-radius: @radius;
    -moz-border-radius: @radius;
    border-radius: @radius;
}

.test_impotant{
    .border_radius()!important;
}
```
```
=====css=====

.test_impotant {
  -webkit-border-radius: 5px !important;
  -moz-border-radius: 5px !important;
  border-radius: 5px !important;
}
```