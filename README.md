<div  align="center">
  <img src="./banner.png"></img>
</div>

<p align="center">
  <a href="http://img.shields.io/travis/txs1992/stylus-converter.svg">
    <img src="http://img.shields.io/travis/txs1992/stylus-converter.svg" />
  </a>
  <a href="https://img.shields.io/npm/dt/stylus-converter.svg">
    <img src="https://img.shields.io/npm/dt/stylus-converter.svg" />
  </a>
  <a href="https://img.shields.io/npm/dm/stylus-converter.svg">
    <img src="https://img.shields.io/npm/dm/stylus-converter.svg" />
  </a>
  <a href="https://img.shields.io/npm/v/stylus-converter.svg">
    <img src="https://img.shields.io/npm/v/stylus-converter.svg" />
  </a>
  <a href="https://img.shields.io/npm/l/stylus-converter.svg">
    <img src="https://img.shields.io/npm/l/stylus-converter.svg" />
  </a>
  <a href="https://img.shields.io/node/v/passport.svg">
    <img src="https://img.shields.io/node/v/passport.svg" />
  </a>
</p>

## Why do this tool

> Since early projects used stylus, stylus is very cool to develop，but the stylus-based indentation code is not very convenient at the time of the modification, plus the team development and use of SCSS, in order to facilitate maintenance and unification, ready to replace the project stylus to SCSS. However, I am very lazy, manual conversion of stylus is a waste of time, and the error rate is large，So this project was born. **Please use your little fortunate hand and give me a `star`. Be grateful.^_^**

## stylus-converter config

### converter options

| Attribute | Description | Type | Accepted Values | Default |
| ---- | ---- | ---- | ---- | ---- |
| `quote` | The quote type to use when converting strings | string | `'` / `"` | `'` |
| `conver` | Conversion type, such as conversion to scss syntax | string | scss | scss |
| `autoprefixer ` | Whether or not to automatically add a prefix, stylus will automatically add prefixes when converting stylus grammars. `@keyframes` | boolean | true / false | true |

### cli options

| Attribute | Shorthand | Description | Accepted Values | Default |
| ---- | ---- | ---- | ---- | ---- |
| `--quote` | `-q` | The quote type to use when converting strings | single / dobule | single |
| `--input` | `-i` | Enter a name, which can be a path to a file or a folder | - | - |
| `--output` | `-o` | Output name, can be a path to a file or a folder | - | - |
| `--conver ` | `-c` | Conversion type, such as conversion to scss syntax | scss | scss |
| `--directory` | `-d` | Whether the input and output paths are directories | yes / no | no |
| `--autoprefixer ` | `-p` | Whether to add a prefix | yes / no | yes |

## Use examples

```javascript
npm install -g stylus-converter

// 运行 cli 转换文件
stylus-conver -i test.styl -o test.scss
```

## 转换文件比较

### 转换前的 stylus 源码

```stylus
handleParams(args...)
  args

@media screen and (max-width: 500px) and (min-width: 100px), (max-width: 500px) and (min-height: 200px)
  .foo
    color: #100

.foo
  for i in 1..4
    @media (min-width: 2 * (i + 7) px)
```

### 转换后的 sass 源码

```scss
@function handleParams($args...) {
  @return $args;
}

@media screen and (max-width: 500px) and (min-width: 100px), (max-width: 500px) and (min-height: 200px) {
  .foo {
    color: #100;
  }
}

.foo {
  @for $i from 1 through 4 {
    @media (min-width: 2 * ($i + 7) px) {
      width: 100px * $i;
    }
  }
}
```

> 如果你不想你转换的 @keyframes 添加默认前缀，请设置 `options.autoprefixer = false`

### 转换前的 `.vue` 文件
```html
<template>
  <div class="page-home">
    <el-button>click me</el-button>
  </div>
</template>

<style lang="stylus">
.page-home
  .el-button
    margin: 10px auto
</style>
```

### 转换后的 `.vue` 文件
```html
<template>
  <div class="page-home">
    <el-button>click me</el-button>
  </div>
</template>

<style lang="scss">
.page-home {
  .el-button {
    margin: 10px auto;
  }
}
</style>
```


## 搭建开发环境

```text
1. 先 fork 项目再 clone 项目到本地
git clone git@github.com:<your github>/stylus-converter.git

2. 进入项目目录
cd stylus-converter

3. 安装项目依赖
npm install

4. 打包编译源文件
npm run build

5. 本地运行 dev 打包并转换 stylus 测试文件
npm run dev
```
