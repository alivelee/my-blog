---
title: Less学习总结
date: ""2020-05-17T05:47:36.583Z""
---

## Less基础

### 变量

和JavaScript类似，找最新的（The Last）的Less变量说明，可以声明在开头，也可以声明在结尾


```
@link-color:        #428bca; // sea blue
@link-color-hover:  darken(@link-color, 10%);

a,
.link {
  color: @link-color;
}
a:hover {
  color: @link-color-hover;
}
```

`@变量名`

这里主要提几个经常用到的，过于冷门移步官方文档
#### 使用在选择器上

```
// Variables
@my-selector: banner;

// Usage
.@{my-selector} {
  font-weight: bold;
  line-height: 40px;
  margin: 0 auto;
}
```

#### 使用在importUrl上

用来规范外部导入less样式文件路径

```
// Variables
@themes: "../../src/themes";

// Usage
@import "@{themes}/tidal-wave.less";
```

#### 变量叠加引用

在特定场景下，用于区分多种主颜色
```
@primary:  green;
@secondary: blue;

.section {
  @color: primary;

  .element {
    color: @@color;
  }
}

.section .element {
  color: green;
}
```

#### 变量的声明位置

```
.lazy-eval {
  width: @var;
}

@var: @a;
@a: 9%;


.lazy-eval {
  width: @var;
  @a: 9%;
}

@var: @a;
@a: 100%;
```

都会编译成

```
.lazy-eval {
  width: 9%;
}
```

#### 可以使用Less属性的值

```
.widget {
  color: #efefef;
  background-color: $color;
}

.widget {
  color: #efefef;
  background-color: #efefef;
}
```