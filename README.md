# PHPStandardDevelop
青蓝成长PHP开发规范

## 摘要

* [1 前言](#1-前言)
* [2 良好的工程结构](#2-良好的工程结构)
* [3 使用DRY原则](#3-使用DRY原则)
* [4 使用有意义并一致命名](#4-使用有意义并一致命名)

### 1 前言
项目是由一个团队来完成，如果没有统一的代码规范，那么每个人的代码必定会风格迥异。多个人同时开发同一模块，等到要整合代码的时候就够你受的了，为了便于后人进行代码阅读和维护，减少程序耦合性，提出了以下PHP开发规范

### 2 良好的工程结构
1. Application为应用入口
2. library为项目库
3. models为模型目录
4. modules为模块目录

```
ucweb
└── application
    └── controllers
        └── Admin
        ├── Api
        ├── Common
        ├── Home
        ├── Course.php
        ├── Error.php
        ├── Index.php
        ├── League.php
        ├── Oauth.php
        ├── User.php
    ├── library
    ├── models
    ├── modules
    ├── plugins
    ├── views
```

### 3 使用DRY原则
#### 3.1 概念
1. Do not Repeat Yourself ：DRY原则指的是不要重复你的代码；
2. write everything twice  ：多次重复打字

#### 3.2 DRY解决办法
1. 拆分可重用函数或类；
2. 使用常量定义；

### 4 使用有意义并一致命名
基本原则：
1. 尽量拒绝拼音；
2. 杜绝没有明确含义的命名：$data2；

#### 4.1 变量命名
1. 变量的名词性：形容词+名词；
2. 长名字可用下划线连接： $new_user;

#### 4.2 函数名
1. 小驼峰式：getUserInfo(…)；
2. 函数的动词性：动词+形容词+名词； 谓语+宾语；

#### 4.3 类的命名
1. 驼峰式：PageManager；
2. 类的名词性：OrderModel；不可出现下划线；

### 5 留空与缩进
缩进应反映出代码的逻辑结构，基本原则：
1. 使用TAB键缩进：不可使用4个空格来代替缩进；
2. 留空：使用空格，换行，空行；

#### 5.1 缩进
1. 被嵌套的逻辑体需要进行缩进；
2. 避免4级以上的缩进，这意味出现了深嵌套；

#### 5.2 空格
参数之间留空格：fopen ($file_location_path, 'w')；

#### 5.3 其他
1. 每行代码不应超过80个字符， 长代码换行：

```php
if ((count($this->languages) == 0) 
	AND isset($_SERVER['HTTP_ACCEPT_LANGUAGE']) 
    AND $_SERVER['HTTP_ACCEPT_LANGUAGE'] != '')；
```

2. 不同逻辑体之间必须空行；
3. 每行最后不允许有空格存在。

### 6 避免代码的Copy&Paste
可能还没理解代码的含义，就呆板的拷贝复制；拷贝来的代码未必就是对的；如果有重复代码，意味着可以拆分出一个功能函数。

### 7 注释
注释块 /**/：
-- 文件头：名称，版权，作者；
-- 类	    ：类作用解释；
-- 函数   ：函数作用，入参数，返回内容；

注释行 //：帮助记忆
-- 代码说明	：一般是用于对某个逻辑块的说明；
-- 结束提示	：长IF，switch，while逻辑体结束说明；
-- 待开发提示：//TODO: 
-- 调试提示	：//DEBUG:

### 8 变量声明和初始化
1. 尽量减少全局变量的声明，需要时可使用config配置文件的方式
2. 避免声明的局部变量覆盖上一级声明的变量
3. 使用前必须将变量初始化化

```php
$number  = 0; //数值型初始化
$string     = ‘’; //字符串初始化
$array     = array(); //数组初始化
```

4. 变量名体现数值类型

```php
$bIsChecked：bool类型；
$iNum：数字型；
```
