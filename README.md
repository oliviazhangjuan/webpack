# webpack
webpack 是一个现代的Javascript 应用程序的模块打包器,当其处理应用程序时，他会递归地构建一个依赖关系图表
## enter
- dependency graph 的入口起点
- 从哪里开始，并遵循着依赖关系图表知道要打包什么
- 单个入口语法
  - entry: string|Array<string>
- 对象语法
  - entry: {[entryChunkName: string]: string|Array<string>}
- 常见场景
  - 分离 应用程序（app）和 公共库（vendor）入口
  - 多个页面应用程序
## output
- 告诉webpack在哪里打包应用程序
- 描述了**如何处理归拢在一起的代码**
- 用法
  - filename:' ' //main.js,bundle.js,index.js
  - path:' '     //绝对路径
- 选项
  - output.chunkFilename
  
    非入口的 chunk(non-entry chunk) 的文件名，路径相对于 output.path 目录。
    
    [id] 被 chunk 的 id 替换。
    
    [name] 被 chunk 的 name 替换（或者，在 chunk 没有 name 时使用 id 替换）。
    
    [hash] 被 compilation 生命周期的 hash 替换。
    
    [chunkhash] 被 chunk 的 hash 替换。
    
  -  output.crossOriginLoading
  
      此选项可以启用跨域加载(cross-origin loading) chunk。

      可选的值有：

      false - 禁用跨域加载

      "anonymous" - 启用跨域加载。当使用 anonymous 时，发送不带凭据(credential)的请求。

      "use-credentials" - 启用跨域加载。发送带凭据(credential)的请求。
   - output.filename
   
      - 单个入口
      - 多个入口
        如果你的配置创建了多个 "chunk"（例如使用多个入口起点或使用类似 CommonsChunkPlugin 的插件），你应该使用以下的替换方式来确保每个文件名都不重复。

        [name] 被 chunk 的 name 替换。

        [hash] 被 compilation 生命周期的 hash 替换。

        [chunkhash] 被 chunk 的 hash 替换。
    - output.path
      - 导出目录为绝对路径（必选项）。
      - [hash] 被 compilation 生命周期的 hash 替换。
      
## loader
- 识别出(identify)应该被对应的 loader 进行转换(transform)的那些文件
- 由于进行过文件转换，所以能够将被转换的文件添加到依赖图表（并且最终添加到 bundle 中）(use 属性)
- loader 支持链式传递。能够对资源使用流水线(pipeline)。loader 链式地按照先后顺序进行编译。loader 链中的第一个 loader 返回值给下一个 loader。在最后一个 loader，返回 webpack 所预期的 JavaScript。
- loader 可以是同步或异步函数。
- loader 运行在 Node.js 中，并且能够执行任何可能的操作。
- loader 接收查询参数。用于 loader 间传递配置。
- loader 也能够使用 options 对象进行配置。
- 除了使用 package.json 常见的 main 属性，还可以将普通的 npm 模块导出为 loader，做法是在 package.json 里定义一个 loader 字段。
- 插件(plugin)可以为 loader 带来更多特性。
- loader 能够产生额外的任意文件。
## plugins
