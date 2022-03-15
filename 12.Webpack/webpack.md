- [webpack(我修改了这个地方)](#webpack我修改了这个地方)
  - [什么是webpack](#什么是webpack)
  - [webpack的作用是什么](#webpack的作用是什么)
  - [webpack核心模块](#webpack核心模块)
  - [webpack常用的loader? 你用过哪些loader](#webpack常用的loader-你用过哪些loader)
  - [webpack常用的plugin? 你用过哪些plugin](#webpack常用的plugin-你用过哪些plugin)
  - [Loader和Plugin的区别？](#loader和plugin的区别)
  - [webpack打包构建流程](#webpack打包构建流程)
  - [Webpack 的热更新原理](#webpack-的热更新原理)
  - [如何对bundle体积进行监控和分析？](#如何对bundle体积进行监控和分析)
  - [Babel原理？](#babel原理)
  - [source map是什么？生产环境怎么用？](#source-map是什么生产环境怎么用)
  - [为什么要代码分割，本质是什么？](#为什么要代码分割本质是什么)
  - [webpack打包优化方案](#webpack打包优化方案)

# webpack(我修改了这个地方)

```txt
https://juejin.cn/post/6844904094281236487
```

## 什么是webpack

>本质上，webpack 是一个用于现代 JavaScript 应用程序的 静态模块打包工具。当 webpack 处理应用程序时，它会在内部从一个或多个入口点构建一个 依赖图，然后将你项目中所需的每一个模块组合成一个或多个 bundles，它们均为静态资源，用于展示你的内容

## webpack的作用是什么

- 模块打包：根据业务把复杂的代码自由划分文件模块，保证打包后项目结构的清晰和可读性。
- 编译兼容：webpack的Loader机制，不仅仅可以帮助我们对代码做polyfill，还可以编译转换诸  如.less， .vue， .jsx这类在浏览器无法识别的格式文件。
- 能力扩展：webpack的Plugin机制，我们在实现模块化打包和编译兼容的基础上，可以进一步实现诸如按需加载，代码压缩等一系列功能。

## webpack核心模块

- (1): 入口（entry）: 项目打包从哪里开始，打包的起点
- (2): 出口（output）: 输出打包的文件的位置，以及名称
- (3): loader: 用于转换某些类型的模块, webpack只能处理js,json类型的文件，其他的类型的文件需要转换成js语言；将内联图片转换成data url
      两个属性：test：识别出哪些类型的文件会被转换；use： 使用哪些loader进行转换，loader执行顺序：从右到左（或从下到上）
- (4): plugin: 代码优化，资源管理
- (5): 模块(modules)：在模块化编程中，开发者将程序分解为功能离散的 chunk，并称之为 模块。

```html

const path = require("path");
const webpack = require("webpack");
const htmlWebpackPlugin = require("html-webpack-plugin");
const { CleanWebpackPlugin } = require("clean-webpack-plugin");
const MiniCssExtractPlugin = require("mini-css-extract-plugin");
const OptimizeCSSAssetsPlugin = require("optimize-css-assets-webpack-plugin");
const PurifyCSS = require('purifycss-webpack')
const glob = require('glob-all')
const SpeedMeasurePlugin = require("speed-measure-webpack-plugin");//分析loader时间
const smp = new SpeedMeasurePlugin();
let publicPath = `https://cdn04.convergemob.com/AD_TEST/VIDEO_TEMPLATE_REACT/ANDROID/`
let template = "./src/template/index.html"
const WebPlugin = require('web-webpack-plugin');

if(process.env.PROTOCAL == '2'){
    publicPath = 'https://cdn04.convergemob.com/AD_TEST/VIDEO_TEMPLATE_REACT_2/ANDROID/'
    template = "./src/template/index_2.html"
}

const config = {
    // 模式，开启相应模式的内置优化
    mode: "production",
    // 打包入口
    entry: {
        index: `./src/index.tsx`
    },
    // 一些包被重复的在一些组件中引用，导致多次打包到了输出的bundle文件中，
    // 通过externals,将一些包不打包进bundle中，而是当使用时，从外部获取扩展。
    // 优点： 避免多次打包相同的package导致的打包后的体积过大
    externals: {},

    // 指定解析文件的方式
    resolve: {
      // 优先查找后缀开始的文件
        extensions: ['.tsx', '.ts', '.js'],
        // 设置优先从哪个文件查找
        modules: [path.resolve(__dirname, "./node_modules")],
        // 引入的路径可以取别名
        alias: {
            "@": path.join(__dirname, "./src")
        },
    },
    output: {
        // 输出的bundle名称，[name]表示使用内部chunck id，entry所对应的index==>> index.js
        filename: "[name].js",
        // 打包的输出文件的存放路径
        path: path.resolve(__dirname, "./dist"),
        chunkFilename: "[name].js",
        // 加载外部资源时的前缀，多数情况下会以/结束，页面中的图片、文件的等会根据出publicpath做相应的调整
        publicPath //指定存放JS⽂件的CDN地址

    },
    // module、chunk、bundle区别
    // 1、打包前的每个文件都是一个module，根据每个文件的依赖关系生成chunk文件，处理好的chunk文件就是bundle文件，为最终源文件，可以在浏览器上直接运行
    // 2、一般来说一个chunk文件对应一个bundle文件，但是当使用其他的转换后，可能一个chunk对应多个bundle，比如把css单独抽离，那么会生成两个bundle
    // 3、直接写出来的是 module，webpack 处理时是 chunk，最后生成浏览器可以直接运行的 bundle。


    // 决定了如何处理不同类型的module文件
    module: {
      // 创建module时匹配数组的规则
        rules: [
            {
                test: /\.tsx?$/,
                include: path.resolve(__dirname, "./src"),
                loaders: ['babel-loader?cacheDirectory=true', 'awesome-typescript-loader']
            },
            {
                test: /\.css$/,
                include: path.resolve(__dirname, "./src"),
                use: [MiniCssExtractPlugin.loader, "css-loader", "postcss-loader"]
            },
            {
                test: /\.scss$/,
                include: path.resolve(__dirname, "./src"),
                use: [{
                    loader: MiniCssExtractPlugin.loader
                }, {
                    loader: "css-loader" // 将 CSS 转化成 CommonJS 模块
                }, {
                    loader: "sass-loader" // 将 Sass 编译成 CSS
                }, {
                    loader: "postcss-loader"
                }]
            },
            {
                test: /\.(png|jpe?g|gif)$/,
                include: path.resolve(__dirname, "./src"),
                use: {
                    loader: "url-loader",
                    options: {
                        name: "[name]-[hash:8].[ext]",
                        outputPath: "images/",
                        limit: 10 * 1024
                    }
                }
            }
        ]
    },
    plugins: [
        new htmlWebpackPlugin({
            title: '激励视频',
            filename: "index.html", //输出的html文件名称
            template, // html模版所在的路径
            minify: {
                // 压缩HTML⽂件
                removeComments: true, // 移除HTML中的注释
                collapseWhitespace: true, // 删除空⽩符与换⾏符
                minifyCSS: true, // 压缩内联css
                //minifyJS: true,
            }
        }),
       // 使用WebPlugin， 可替代上面的生成模版, 一个WebPlugin对应一个html文件，管理多个单页面应用，每个单页面生成不同的html
       new WebPlugin({
         template: template,
         filename: 'index.html'
       })

        //抽离css
        new MiniCssExtractPlugin({
            filename: "[name].css"
        }),
        new OptimizeCSSAssetsPlugin({
            cssProcessor: require("cssnano"), //引⼊cssnano配置压缩选项
            cssProcessorOptions: {
                discardComments: { removeAll: true }
            }
        }),
        // 清除⽆⽤ css
        new PurifyCSS({
            paths: glob.sync([
                // 要做 CSS Tree Shaking 的路径⽂件
                path.resolve(__dirname, `./src/**/*.tsx`),
                path.resolve(__dirname, './src/*.html'), // 请注意，我们同样需要对 html ⽂件进⾏ tree shaking
            ])
        }),
    ],
    optimization: {
      // 1、最初的chunks之间的关系是通过webpack之间的图谱关系依赖的，可能存在重复依赖的情况
      // 2、splitChunks配置如何进行chunk的拆分
      // 3、拆分规则：新的chunk可以被共享，或者模块来自于node_modules文件，体积大于一定的大小，初始化加载并行数量、按需加载并行数量最大数量小于或等于 30

        splitChunks: {
            chunks: "all", // 所有的 chunks 代码公共的部分分离出来成为⼀个单独的⽂件，在异步和非异步 chunk 之间共享
        },
    },
}
module.exports = smp.wrap(config);
```

## webpack常用的loader? 你用过哪些loader

- babel-loader: 把 ES6 转换成 ES5
- css-loader：加载 CSS，支持模块化、压缩、文件导入等特性
- sass-loader：将SCSS/SASS代码转换成CSS
- ts-loader: 将 TypeScript 转换成 JavaScript
- awesome-typescript-loader：将 TypeScript 转换成 JavaScript，性能优于 ts-loader
- style-loader：把 CSS 代码注入到 JavaScript 中，通过 DOM 操作去加载 CSS
- file-loader：把文件输出到一个文件夹中，在代码中通过相对 URL 去引用输出的文件 (处理图片和字体)
- url-loader：与 file-loader 类似，区别是用户可以设置一个阈值，大于阈值会交给 file-loader 处理，小于阈值时返回文件 base64 形式编码 (处理图片和字体)
- eslint-loader：通过 ESLint 检查 JavaScript 代码是否符合编码规范和统一的代码风格；审查代码是否存在语法错误；
- postcss-loader：扩展 CSS 语法，使用下一代 CSS，可以配合 autoprefixer 插件自动补齐 CSS3 前缀

## webpack常用的plugin? 你用过哪些plugin

- html-webpack-plugin：简化 HTML 文件创建 (依赖于 html-loader)
- web-webpack-plugin：可方便地为单页应用输出 HTML，比 html-webpack-plugin 好用
- uglifyjs-webpack-plugin：不支持 ES6 压缩 (Webpack4 以前)
- terser-webpack-plugin: 支持压缩 ES6 (Webpack4)
- webpack-parallel-uglify-plugin: 多进程执行代码压缩，提升构建速度
- mini-css-extract-plugin: 分离样式文件，CSS 提取为独立文件，支持按需加载 (替代extract-text-webpack-plugin)
- speed-measure-webpack-plugin: 可以看到每个 Loader 和 Plugin 执行耗时 (整个打包耗时、每个 Plugin 和 Loader 耗时)
- webpack-bundle-analyzer: 可视化 Webpack 输出文件的体积 (业务组件、依赖第三方模块)

## Loader和Plugin的区别？

- Loader 本质就是一个函数，在该函数中对接收到的内容进行转换，返回转换后的结果。
因为 Webpack 只认识 JavaScript，所以 Loader 就成了翻译官，对其他类型的资源进行转译的预处理工作。
- Plugin 就是插件，基于事件流框架 Tapable，插件可以扩展 Webpack 的功能，在 Webpack 运行的生命周期中会广播出许多事件，Plugin 可以监听这些事件，在合适的时机通过 Webpack 提供的 API 改变输出结果。
- Loader 在 module.rules 中配置，作为模块的解析规则，类型为数组。每一项都是一个 Object，内部包含了 test(类型文件)、loader、options (参数)等属性。
- Plugin 在 plugins 中单独配置，类型为数组，每一项是一个 Plugin 的实例，参数都通过构造函数传入。

## webpack打包构建流程

```txt
初始化参数：从配置文件和 Shell 语句中读取与合并参数，得出最终的参数；
开始编译：用上一步得到的参数初始化 Compiler 对象，加载所有配置的插件，执行对象的 run 方法开始执行编译；
确定入口：根据配置中的 entry 找出所有的入口文件；
编译模块：从入口文件出发，调用所有配置的 Loader 对模块进行翻译，再找出该模块依赖的模块，再递归本步骤直到所有入口依赖的文件都经过了本步骤的处理；
完成模块编译：在经过第4步使用 Loader 翻译完所有模块后，得到了每个模块被翻译后的最终内容以及它们之间的依赖关系；
输出资源：根据入口和模块之间的依赖关系，组装成一个个包含多个模块的 Chunk，再把每个 Chunk 转换成一个单独的文件加入到输出列表，这步是可以修改输出内容的最后机会；
输出完成：在确定好输出内容后，根据配置确定输出的路径和文件名，把文件内容写入到文件系统。

简单概括：
初始化：启动构建，读取与合并配置参数，加载 Plugin，实例化 Compiler
编译：从 Entry 出发，针对每个 Module 串行调用对应的 Loader 去翻译文件的内容，再找到该 Module 依赖的 Module，递归地进行编译处理
输出：将编译后的 Module 组合成 Chunk，将 Chunk 转换成文件，输出到文件系统中

```

## Webpack 的热更新原理

```txt
Webpack 的热更新又称热替换（Hot Module Replacement），缩写为 HMR。 这个机制可以做到不用刷新浏览器而将新变更的模块替换掉旧的模块。通过以下方式来加快开发速度：
- 保留在完全重新加载页面期间丢失的应用程序状态。
- 只更新变更内容，以节省宝贵的开发时间。
- 在源代码中 CSS/JS 产生修改时，会立刻在浏览器中进行更新，这几乎相当于在浏览器 devtools 直接更改样式。

```

HMR的核心就是浏览器从服务端拉取更新后的文件，通过chunk diff来更新变化后的修改。
大概流程是我们用webpack-dev-server启动一个服务之后，浏览器和服务端之间维护了一个Websocket长连接，webpack内部实现的watch就会监听文件修改，只要有修改，webpack会重新打包编译到内存中，然后webpack-dev-server依赖中间件webpack-dev-middleware和webpack之间进行交互，每次热更新webpack-dev-server都会带上hash值的json文件和一个js向浏览器推送更新，让浏览器与上一次资源进行对比。浏览器对比出差异后会向 webpack-dev-server 发起 Ajax 请求来获取更改内容(文件列表、hash)，这样客户端就可以再借助这些信息继续向 WDS 发起 jsonp 请求获取该chunk的增量更新，至于内部原理，因为水平限制，目前还看不懂。

## 如何对bundle体积进行监控和分析？

webpack-bundle-analyzer 生成 bundle 的模块组成图，显示所占体积

## Babel原理？

- 大概可以概括为三部分

  - 解析（parse）：将代码（字符串）转换成AST
    - 将代码解析成抽象语法树（AST），每个js引擎（比如Chrome浏览器中的V8引擎）都有自己的AST解析器，而Babel是通过Babylon实现的。在解析过程中有两个阶段：词法分析和语法分析，词法分析阶段把字符串形式的代码转换为令牌（tokens）流，令牌类似于AST中节点；
    语法分析阶段则会把一个令牌流转换成 AST的形式，同时这个阶段会把令牌中的信息转换成AST的表述结构。
  - 转化（transform）：访问AST节点进行转换生成新的AST
    - 在这个阶段，Babel接受得到AST并通过babel-traverse对其进行深度优先遍历，在此过程中对节点进行添加、更新及移除操作。这部分也是Babel插件介入工作的部分。
  - 生成（generate）：以新的AST为基础将转换为代码
    - 将经过转换的AST通过babel-generator再转换成js代码，过程就是深度优先遍历整个AST，然后构建可以表示转换后代码的字符串。

## source map是什么？生产环境怎么用？

- 项目一般是将源码经过编译、打包、压缩等转换后，部署到生产环境，但是，当需要debug的时候，打包压缩后的代码不具备良好的可读性。
- source map 是将编译、打包、压缩后的代码映射回源代码的过程。使得调试代码变得简单。
  
- 线上环境一般有三种处理方案:
  (1)hidden-source-map：可以查看错误代码准确信息，但不能追踪源代码错误，只能提示到构建后代码的错误位置。借助第三方错误监控平台 Sentry 使用
  (2)sourcemap：可以查看错误代码准确信息和源代码的错误位置。通过 nginx 设置将 .map 文件只对白名单开放(公司内网)
  (3)nosources-source-map：只会显示具体行数以及查看源代码的错误栈。安全性比 sourcemap 高

- 配置： devtool: 'source-map'

## 为什么要代码分割，本质是什么？

打包是将一个文件所有的引用合并到一个单独的文件中，最终形成一个bundle，在页面上script引入这个bundle，整个应用就可以一次性加载。
随着你的应用代码包量增长。尤其是在整合了体积巨大的第三方库的情况下会造成：bundle因体积过大会导致首屏加载时间过长；项目中依赖文件过多，而导致 http 请求过多的问题。

本质：用可接受的服务器性能压力增加来换取更好的用户体验
打包成唯一脚本：一把请求完，后续服务器压力小，但是请求时间长，页面空白期长，用户体验不好。

## webpack打包优化方案

一般来说，影响webpack打包性能的因素：构建过程时间太长，打包结果体积太大

- 提升构建速度
  (1)优化loader配置
  - 缩小文件搜索范围，使用include和exclude指定或者排除需要loader搜索的路径
  - 缓存Babel 编译过的文件，下次只需要编译更改过的代码文件即可，加快打包时间

  ```html
  module.export = {
    module: {
        rules: {
                test: /\.js$/,
                include: path.resolve(__dirname, "./src"),
                exclude: /node_modules/,
                use: [{
                    loader: "babel-loader?cacheDirectory=true" 
                }]
            },
        }
   }
  ```

  (2)合理使用resolve
  对webpack 的 resolve 参数进行合理配置，使用 resolve 字段告诉 webpack 怎么去搜索文件。
  - resolve.extensions:导入语句没带文件后缀时，webpack 会自动带上后缀后去查找文件是否存在，查询的顺序是按照配置的 resolve.extensions 顺序从前到后查找。所以应该将出现频率高的后缀排在前面
  - resolve.alias:给导入路径取一个别名，能把原导入路径映射成一个新的导入路

  ```html
  const config = {
    resolve: {
        extensions: ['.tsx', '.ts', '.js'],
        alias: {
            "@": path.join(__dirname, "./src")
        },
    },
  }
  ```

  (3)压缩代码
  - webpack-paralle-uglify-plugin 并行运行 UglifyJS压缩代码
  - uglifyjs-webpack-plugin 开启 parallel 参数 (不支持ES6, webpack4之前)
  - terser-webpack-plugin 开启 parallel 参数(支持es6，webpack4)
  - 通过 mini-css-extract-plugin 提取 Chunk 中的 CSS 代码到单独文件，通过 css-loader 的 minimize 选项开启 cssnano 压缩 CSS。

  (4)DllPlugin插件 提前打包类库（预编译）
  DllPlugin可以将类库提前打包并引入。在首次构建时将第三方库单独打包到一个文件中（eg: react， antd， moment等库），只有当类库更新版本才有需要重新打包，这种方式可以极大的减少打包类库的次数。同时也将公共代码抽离成单独的文件。
  - 步骤一：单独配置一个webpack.dll.config.js 文件，打包第三方库代码

  ```html
  const webpack = require('webpack');
  const path = require('path');

  // 想统一打包的类库
  const vendors_manage = [
  'react','react-dom','moment','bizcharts', 'antd', 'lodash', 'underscore'];

  module.exports = {
    output: {
      path: path.resolve(__dirname, 'public'),
      filename: '[name].dll.js',
      library: '_dll_[name]', 
    },
    entry: {
      vendors_manage,
    },
    plugins: [
      new webpack.DllPlugin({
          name: '_dll_[name]',  // DllPlugin的name属性需要和output.libary保持一致
          path: 'manifest.json',
          context: __dirname,  // context需要和DllReferencePlugin中的保持一致
      }),
    ],
  };

  ```

  - 步骤二：在webpack.config.js中，打包项目代码
  
  ```html
  const webpack = require('webpack')
  module.exports = function wp(webpackConfig)（{
      webpackConfig.plugins.push(new webpack.DllReferencePlugin({
          context: __dirname,
          // manifest.json 就是之前打包出来的 json 文件
          manifest: require('./manifest.json')
        }),
        
    })
  }）

  ```

  npm run build:dll 运行这个配置文件，dist里会出现vendors_manage.dll.js模块库文件和manifest.json模块映射文件其中vender-menifest.json标明了模块路径和模块ID（由webpack产生）的映射关系。

  ```html
  {
    "name": '_dll_vendors_manage'
    "content": {
      './node_modules/.npminstall/loadsh/4.17.2/loadsh/loadsh.js':1
      './node_modules/.npminstall/webpack/1.17.2/webpack/module.js':2
      './node_modules/.npminstall/react/16.17.2/react/react.js':3
    }
  }
  ```

  (5) happypack多进程编译
  受限于 Node 是单线程运行的，所以 Webpack 在打包的过程中也是单线程的，特别是在执行 Loader 的时候，长时间编译的任务很多，这样就会导致等待的情况。

  ```html
  const webpack = require('webpack')
  const HappyPack = require('happypack');

  module.exports = {
      plugins: [
      new HappyPack({
          // id标识happypack处理那一类文件
          id: 'happyBabel',
          // 配置loader
          loaders: ['babel-loader?cacheDirectory=true'],
        })
      ],
      module: {
          rules: [
              {
                  test: /\.js$/,
                  loader: 'happypack/loader?id=happyBabel',
                  // 将.js文件交给id为happyBabel的happypack实例来执行
              },
          ]
      }
  }

  ```
