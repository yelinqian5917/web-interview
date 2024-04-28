# webpack

## wabpack 是做什么的？
概念：webpack 是一个用于现代 JavaScript 应用程序的 静态模块打包工具。当 webpack 处理应用程序时，它会在内部从一个或多个入口点构建一个 依赖图(dependency graph)，然后将你项目中所需的每一个模块组合成一个或多个 bundles，它们均为静态资源，用于展示你的内容

原理： 从入口开始递归的开始读取模块所依赖的的文件内容，生成 AST 树，然后遍历 AST 树，输出让浏览器能够运行的代码到 dist 文件夹

> 抽象语法树（Abstract Syntax Tree，简称AST）是源代码的抽象语法结构在计算机内存中的表现形式。它是编译器或解释器在处理源代码时所使用的一种中间表示形式。AST在编译和代码生成过程中起着关键作用。

## webpack的打包流程

1. 读取配置文件。首先，Webpack会读取项目中的webpack.config.js文件，解析其中的配置信息，以便后续的打包过程可以按照这些配置来进行。

2. 找到入口文件。解析配置文件之后，Webpack会根据配置中的入口文件来寻找项目的起始点。入口文件是一个JavaScript文件，Webpack会从这个文件开始递归地解析项目中的所有依赖关系。

3. 解析依赖模块。找到入口文件之后，Webpack会递归地解析项目中的所有依赖模块，包括JavaScript文件、CSS文件、图片文件等等。Webpack使用不同的加载器(loader)来解析不同类型的文件。

4. 编译模块。解析依赖模块之后，Webpack会使用相应的loader来编译这些模块。编译过程中，Webpack可以对模块进行处理，例如转译ES6、压缩代码、提取公共模块等等。

5. 合并模块。在编译完成之后，Webpack会将所有模块合并成一个或多个包(bundle)。Webpack可以根据配置中的规则来将模块分组打包，以便于在浏览器中加载和运行。

6. 输出文件。在合并模块完成之后，Webpack会将最终的包输出到指定的目录下，以便于在浏览器中加载和运行。输出的文件可以是JavaScript文件、CSS文件、图片文件等等。

## loader 与 plugin 的区别
webpack 将一切都视为模块，但是 webpack 原生只能解析 js 文件和 json 文件，如果要解析其他类型的文件就要用到 loader，所以loader 相当于翻译官的作用，将其他类型的文件进行预处理

Plugin 为插件的意思，Plugin 可以扩展 webpack 的功能，在 Webpack 运行的生命周期中会广播出许多事件，Plugin 可以监听这些事件，帮助 webpack 做一些事情。

## 常用的 plugin
html-webpack-plugin 这个插件会创建一个 html 文件，并且会自动的引入打包好的文件资源
mini-css-extract-plugin 打包过后的 css 在 js 文件里，该插件可以把 css 单独抽出来

## 怎么利用 webpack 来优化网页性能
资源文件压缩
Tree Shaking
代码分离
动态导入代码（懒加载、预获取）
缓存

## 如何提高代码构建速度
优化 loader 配置，缩小处理范围:合理利用这两个属性 exclude：不需要处理的文件 和 include：需要处理的文件
HMR(Hot Module Replacement) 模块热替换只重新构建发生变化的模块
babel 缓存 第二次构建时，会读取之前的缓存，只重新构建变化的文件
使用 Dll 进行分包
多进程打包

## 


## 链接
https://zhuanlan.zhihu.com/p/578899982

https://zhuanlan.zhihu.com/p/443964387?utm_id=0

## 优化篇
https://blog.csdn.net/qq_32057581/article/details/122324420
