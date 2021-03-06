title: AMD Turn Over? Meltdown and Spectre
speaker: yaoj
transition: horizontal
files: /js/demo.js

[slide style="background-image:url('/headless-chrome/cover.png')"]

# <div class="cover title">Meltdown and Spectre<div>
## <div class="cover author">演讲者：yaoj<div>

<style>
.cover {
    font-family: 'Consolas';
    color: #333;
}
.cover.title {
    font-size: 72px;
}
.cover.author {
    font-size: 42px;
}
</style>

[slide style="background-image:url('/headless-chrome/horseman.png')"]

# 先说是什么 {:&.flexbox.vleft}

[slide style="background-image:url('/headless-chrome/headless.png')"]

# 无UI的浏览器  {:&.flexbox.vright}
## 开局一个CONSOLE，控制全靠命令

[slide style="background-image:url('/headless-chrome/three.png')"]
<br/>
## <span class="three">提供DOM环境模拟，允许执行DOM API操作</span>
## <span class="three">提供完整JS运行环境</span>
## <span class="three">    ↓↓↓↓  </span>
## <span class="three">前端测试容器、预渲染</span>
<style>
.three {
    display: inline-block;
    width: 1080px;
    font-size: 40px;
    color:#666;
    margin: -500px;
}
</style>

[slide style="background-image:url('/headless-chrome/language.png')"]

# 无头浏览器都有啥

## 全平台
### PhantomJS - Command line/all platforms.
<br/>
<div style="display:flex;font-size: 21px;">
    <section style="width: 50%;">
        <h2>Python</h2>
        <ul>
            <li>Spynner - Python only.</li>
            <li>Ghost - Python only.</li>
            <li>Twill - Python/command line.</li>
            <li>Ghost - Python only.</li>
            <li>Twill - Python/command line.</li>
        </ul>
    </section>
    <section style="width: 50%;">
        <h2>Others</h2>
        <ul>
            <li>HtmlUnit - Java.</li>
            <li>Awesomium - C++/.Net/all platforms.</li>
            <li>SimpleBrowser - .Net 4/C#.</li>
            <li>ZombieJS - Node.js.</li>
            <li>EnvJS - JavaScript via Java/Rhino.</li>
            <li>Watir-webdriver with headless gem - Ruby via WebDriver.</li>
        </ul>
    </section>
</div>

[slide style="background-image:url('/headless-chrome/web.png')"]

# 爬个虫/蜘个蛛

对比传统的HttpClient模式

## 优势

- 可以抓取动态JS页面
- 真实模拟浏览器环境，不需要搞伪装，当然IP不能省
- 真实模拟浏览器环境，简单方便
- 灵活性强，大不了我截个图你能咋滴

## 劣势

- 真实模拟浏览器环境，自身速度慢
- 真实模拟浏览器环境，网络请求多，速度慢
- 不适合分布式大规模抓取

[slide style="background-image:url('/headless-chrome/chrome.png')"]

# Google Chrome/puppeteer {:&.flexbox.vleft}
## 官方杀死同人系列
https://github.com/GoogleChrome/puppeteer


[slide style="background-image:url('/headless-chrome/p-b.png')"]
<div style="display:flex; margin-left: -200px;">
    <div style="width:290px; height:424px;background: url('/headless-chrome/puppeteer.png')"></div>
    <div style="width: 750px; margin-left: 100px;" class="list-f">
        <div>- 自带截图生成PDF API</div>
        <div>- 为SPA应用做预渲染</div>
        <div>- 爬虫</div>
        <div>- 自动表单填写，UI测试，模拟键盘输入</div>
        <div>- 及时更新的自动化的测试环境，随时在最新的Chrome环境中运行，享受最新的浏览器特性与JS功能</div>
        <div>- 输出时间轴标记用于浏览器性能测试</div>
        <div>- 基于DevTools protocol, 理论上devTools有的东西都能玩</div>
    <div>
</div>
<style>
    .list-f>div {
        text-align:left;
        margin: 30px 10px;
    }
</style>

[slide style="background: #333"]
### 截图-代码范例
```js
// 获取浏览器
const browser = await puppeteer.launch();
// 打开TAB
const page = await browser.newPage();
// 输入URL
await page.goto('https://www.t66y.com');
// 等待页面完全打开
console.log(await page.content());
// 截图
await page.screenshot({path: 'screenshot.png'});
// 关闭
await browser.close();
```

[slide style="background: #555"]
### 运行JS-代码范例
```js
// 获取浏览器
const browser = await puppeteer.launch();
// 打开TAB
const page = await browser.newPage();
 // 跳转URL
await page.goto('https://www.baidu.com')
// 等待 #kw DOM节点可用
await page.waitFor('#kw')
// 往页面内注入JS
await page.evaluate((_query) => {
    // 输入搜索关键字
    document.querySelector('#kw').value = _query
    // 点击搜索按钮
    document.querySelector('#su').click()
}, query)
// 等待网络空闲，说明搜索完成
await page.waitForNavigation({
    waitUntil: 'networkidle',
})
// 注入JS抓取本页搜索结果内容
const searchResult = await page.evaluate(getData)
// 注入JS抓取分页信息
const pageData = await page.evaluate(getPages)
return { searchResult, pageData }
```

[slide style="background: #777"]
### 一些技巧1
```js
// 获取浏览器
const browser = await puppeteer.launch({
    headless: false //显示浏览器
    executablePath: './static/chrome-win32/chrome.exe' // 本地chrome浏览器
});
// 打开TAB
const page = await browser.newPage();
// 设置拦截过滤器
await page.setRequestInterceptionEnabled(true)
page.on('request', (interceptedRequest) => {
    if (interceptedRequest.resourceType === 'stylesheet'
        || /token/.test(interceptedRequest.url)) {
        interceptedRequest.abort()
    } else {
        interceptedRequest.continue()
    }
})
```

[slide style="background: #999"]
### 一些技巧2
```js
// 获取浏览器
// 设置拦截过滤器
await page.setRequestInterceptionEnabled(true)
page.on('request', (interceptedRequest) => {
    if (interceptedRequest.resourceType === 'stylesheet'
        || /token/.test(interceptedRequest.url)) {
        interceptedRequest.abort()
    } else {
        interceptedRequest.continue()
    }
})
```
[slide style="background: #bbb"]
### 一些技巧3
```js
// 模拟键盘
await page.keyboard.type('Hello World!')
await page.keyboard.press('ArrowLeft')
// 模拟鼠标
await mouse.click(300, 720, {
    button: 'left'
})
```
[slide style="background-image:url('/headless-chrome/pan.png')"]
# 坑坑坑 {:&.flexbox.vleft}

<div class="list-pan">
        <div>- 不翻墙，下不了自带的Chromium内核</div>
        <pre style="width: 500px;margin: 0 0 0 800px;">
            <code class="js hljs javascript">npm set PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=<span class="hljs-literal">true</span>
        </code></pre>
        <div>- 继承Chrome的版本帝，更新极为频繁</div>
        <div>- 瞎生成缓存文件，浪费硬盘空间</div>
<div>

<style>
    .list-pan {
        text-align: right;
        position: absolute;
        color: #333;
        right: -300px;
    }
    .list-pan > div {
        font-size: 40px;
        margin: 30px;
    }
</style>

[slide style="background-image:url('/headless-chrome/flash.png')"]
# 实战 {:&.flexbox.vleft}

## 抢车票，抢小米，抢卷，抢TM的
## 刷票刷分刷评价，刷TM的
## 下资源下种子合集，下TM的
## 抓内容，监听更改，偷TM的
</style>
