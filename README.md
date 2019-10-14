# my-project

> A Mpvue project

## Build Setup

``` bash
# 初始化项目
vue init mpvue/mpvue-quickstart myproject
cd myproject

# 安装依赖
yarn

# 开发时构建
npm dev

# 打包构建
npm build

# 指定平台的开发时构建(微信、百度、头条、支付宝)
npm dev:wx
npm dev:swan
npm dev:tt
npm dev:my

# 指定平台的打包构建
npm build:wx
npm build:swan
npm build:tt
npm build:my

# 生成 bundle 分析报告
npm run build --report
```

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).


小程序中强烈推荐使用flex布局进行编写


※ 注意事项
1. 在每个组建中都需要使用: 组件实例$mount() 去挂载当前组件,否则对应的页面不能生效
2. npm run dev 每次都会重新打包dist文件, 测试只能在小程序工具上
3. mpvue中绑定小程序原生事件不能使用bind + 事件名, 需要使用@事件名, 且要定义在methods中, 否则不生效
4. 新创建的新页面要重新执行: npm run dev 才能生效

不建议使用小程序中的生命周期函数


小程序中默认有两种绑定事件的方式: bind(冒泡事件)  catch(非冒泡事件)

两种常用的导航的方式:
```js
wx.navigateTo({ url: '/page/list/main' })
wx.switchTab({ url: '/page/list/main' })
```

小程序中不支持使用axios, 会报错: XMLHttpRequest is not a constructor
原因是: **小程序的环境和浏览器的环境不一样
解决方案是: 使用其他的库: flyio


### 原生小程序和 mpvue开发小程序的对比
1. 原生小程序运行更稳定些, 兼容性好, mpvue可能在某些方面存在兼容性的问题(比如vue-router)
2. mpvue 支持vue组价化开发, 效率更高, 功能强大
3. mpvue 可基于webpack组件化, 工程化开发
4. 原生不支持npm安装包, 不支持css预处理
5. 支持computed计算属性, 和watcher监听器, 模板语法中, 只简单的支持js表达式



