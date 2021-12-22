title: NPM && NPM Register
speaker: yaoj@landicorp.com
plugins:
    - echarts

<slide class="bg-black-blue fullscreen aligncenter" image="https://wallpapers.wallhaven.cc/wallpapers/full/wallhaven-703949.jpg dark">

<div style="padding-top: 500px">
# NPM 包管理器 {.text-landing.text-shadow}
# NPM 私有服务器 {.text-landing.text-shadow}
</div>

</slide>

<slide class="bg-black-blue aligncenter" image="https://wallpapers.wallhaven.cc/wallpapers/full/wallhaven-665745.jpg .dark">

# Webpack Demo {.text-landing.text-shadow.animated.fadeInDown.delay-800}

https://github.com/ruanyf/webpack-demos {.text-intro}

[:fa-github: Github](https://github.com/ksky521/nodeppt){.button.ghost}

</slide>

<slide class="aligncenter bg-gradient-v">

:::
## 包管理器 -- 结束过去手工共享代码的日子
## 同时npmjs.com也是一个商业站点
:::

</slide>

<slide class="bg-gradient-h aligncenter">


::: column

## 对比Maven

:::flexblock {.specs}

::fa-copy::

## 局部依赖而非全局依赖

空间不值钱，方便复制移动
直接规避了多版本共存的问题

---
::fa-align-right::

## 扁平化排布

过去的深度排布，炸了Linux的文件系统

---
::fa-file::

## 即是源代码也是库

随你修改，不影响其他项目

:::


</slide>

<slide class="bg-gradient-r aligncenter">
## 生成一个包

---

:::shadowbox

## npm init [/y]

将当前目录变成一个包，其实就是生成一个`package.json`文件

---

## package.json

描述包信息，至少包含以下字段

name 包名称

version 版本

:::

<slide class="bg-gradient-h aligncenter">


::: column

## 依赖关系

:::flexblock {.specs}

::fa-copy::

## dependencies

项目运行所需要的库 --save, -s, --save-prod-, -P

---
::fa-align-right::

## devDependencies

项目开发所需要的库 --save-dev, -D

---
::fa-file::

## peerDependencies

前置需求的库，不被安装，但是会提示缺少(废弃)

---
::fa-arrows-h::

## optionalDependencies

可选依赖，不被安装，但是会提示缺少 --save-optional, -o

---
::fa-arrows-v::

## bundledDependencies

打包依赖，发布时会一起打包

:::

<slide class="bg-gradient-v aligncenter">


::: column

## 重要字段

:::flexblock {.specs}

::fa-align-right::

## main

包的入口，用于require('')时返回的入口对象

---
::fa-copy::

## bin

安装时候将生成命令行入口程序

---
::fa-file::

## script

包指令，用于`npm run`执行对应的指令

:::

<slide class="bg-gradient-r aligncenter">


::: column

## 常用命令

```https://docs.npmjs.com/cli-documentation/cli```

:::flexblock {.specs}

::fa-align-right::

## npm install [packageName][@version]

安装依赖包

---
::fa-copy::

## npm update [packageName]

更新依赖包

---
::fa-file::

## npm uninstall [packageName]

删除依赖包

---
::fa-plus::

## npm publish

发布依赖包

---
::fa-remove::

## npm unpublish [packageName][@version]

删除发布依赖包

<slide class="bg-trans-light aligncenter">

## 配置命令
<style>
pre {
    font-size: 3rem;
}
</style>
<div class="dd">
```
npm config set <key> <value> [-g|--global]
npm config get <key>
npm config delete <key>
npm config list [-l] [--json]
npm config edit
```
</div>

<slide class="bg-blue aligncenter">

# @scope/packageName

<slide class="bg-light aligncenter">

```
// 设置联迪域的地址
npm config set @landi:registry http://10.10.30.186:4873
// 增加账号
npm adduser --registry http://10.10.30.186:4873
```

<slide class="bg-light aligncenter">
# npm version

`修改package.json，生成git commit， 生成tag 三合一`

```
npm version [<newversion> | major | minor | patch
| premajor | preminor | prepatch 
| prerelease [--preid=<prerelease-id>] | from-git]

'npm view <pkg> version' to view a package's published version
```

<slide class="bg-secondary aligncenter">

# 免费私有NPM服务器
## https://verdaccio.org/
## https://github.com/cnpm/cnpm

<slide class="bg-apple aligncenter">

# 区别

### Database
### Owner/Register
### KPI
