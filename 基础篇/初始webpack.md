## 初始webpack配置组成
~~~ javascript
module.exports = {
    entry: './src/index.js', // 打包的入口文件
    output: './dist/main.js', // 打包的输入
    mode: 'production', // 环境
    module: {
        rules: [ // Loader配置
            { test: /|.txt$/, use: 'raw-loader' }
        ]
    },
    plugins: [ //插件配置
        new HtmlwebpackPlugin({template: './src/index.html'})
    ]
}
~~~

## entry 
依赖图的入口是entry,对非代码比如图片，文字以来也会不断加入到依赖图中

## output
output 用来告诉webpack如何将编译后的文件输出到磁盘

## loaders （核心概念）
webpack开箱即用只支持js和json两种文件类型，通过loaders去支持其他文件类型并且将他们转化为有效的模块，并且可以添加到依赖图中  
本身是一个函数， 接受原文件作为参数， 返回转换的结果  
css-loader用于加载.css文件，并且转换成commonjs对象  
style-loader将样式通过\<style\>标签插入到head中
* loader是从右到左进行的链式调用，所以loader的顺序是很重要的

## Plugins (核心概念)
插件用于bundle文件的优化，资源管理和环境变量注入；作用于整个构建过程。

## mode (核心概念)
mode用来指定当前的构建环境是：production、development还是none  
设置mode可以使用webpack内置的函数，默认值为production

## watch (文件监听)
**文件监听的原理分析**
轮询判断文件的最后编辑时间是否变化，某个文件发生了变化，并不会立即告诉监听者，而是先缓存起来等aggregateTimeout
~~~ javascript
module.export = {
    // 默认false,也就是不开启
    watch: true,
    watchOptions: {
        // 默认为空， 不监听的文件或文件夹，支持正则匹配
        ignored: /node_modules/,
        // 监听到变化后会等300ms再去执行，默认是300ms
        aggregateTimeout: 300,
        // 判断文件是否发生变化是通过不断询问系统指定文件有没有变化产生实现的，默认每秒问1000次
        poll: 1000
    }
}
~~~

## webpack-dev-server (热更新)

WDS直接输出到内存，不会与磁盘进行IO操作   

**HotModuleReplacementPlugin插件**

**热更新的原理分析**  
此处缺失图片
* **wbepack Compile:** 将JS编译成Bundle
* **HMR server:** 将热更新的文件输出给HMR Runtime
* **Bundle server:** 提供文件在浏览器的访问
* **HMR Runtime:** 会被注入到浏览器，更新文件的变化
* **bundle.js:** 构建输出的文件

## 文件指纹
**文件指纹**是在打包后输出的文件名中特定标识版本等信息的后缀  
### 文件指纹如何生成
* **Hash:** 和整个项目的构建相关，只要项目文件有改动，整个项目的构建的hash值就会更改
* **Chunkhash:** 和wenpack打包的chunk有关，不同的entry会生成不同的chunkhash的值
* **Contenthash:** 根据文件内容来定义hash， 文件内容不变，则contenthash不变