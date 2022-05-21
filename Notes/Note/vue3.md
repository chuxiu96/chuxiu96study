## 〇、教学视频

[黑马Vue3.0](https://www.bilibili.com/video/BV1zq4y1p7ga?p=290)

## 一、vue3安装

https://24kcs.github.io/vue3_study/

### 1 - 独立版本

在 Vue.js 的官网上直接下载 vue.min.js 并用 **<script>** 标签引入。

### 2 - CDN

- 对于制作原型或学习，你可以这样使用最新版本
- 对于生产环境，推荐链接到一个明确的版本号和构建文件，以避免新版本造成的不可预期的破坏

```html
<script src="https://unpkg.com/vue@next"></script>
```

### 3 - npm

- 用 Vue 构建大型应用时推荐使用 npm 安装

    ```bash
    # 最新稳定版
    $ npm install vue@next
    ```

### 4 - 使用官方配套开发工具来构建一个 vue 项目

#### 4.1 - 命令行工具（ [CLI](https://www.javascriptc.com/vue3js/guide/installation.html#cli) ）

Vue 提供了一个官方的CLI，为单页面应用 (SPA) 快速搭建繁杂的脚手架。

##### 4.1.1 - 使用 @vue/cli 创建 vue 项目

- 全局安装最新版本的 @vue/cli

```sh
# 全局安装最新版本的 @vue/cli
$ npm install -g @vue/cli
# OR
$ yarn global add @vue/cli

# 升级全局的 vue/cli包
$ npm update -g @vue/cli
# OR
yarn global upgrade --latest @vue/cli
```

- 安装完后查看版本

```sh
$ vue --version
@vue/cli 5.0.4
# 要求 @vue/cli 版本在4.5.0以上
```

- 创建项目

```sh
# 创建项目
$ vue create my-project

# 使用可视化创建工具来创建项目
$ vue ui
```

- 在 Vue 项目中运行

```sh
$ vue upgrade --next
```

***

##### 4.1.2 - 使用 CLI 创建项目的流程梳理

-  全局安装最新版本的 @vue/cli

    > ```sh
    > $ npm install -g @vue/cli
    > ```

- 创建项目

    > ```sh
    > $　vue create <项目名>
    > ```

- 选取一个preset

    ![vue preset](https://cli.vuejs.org/cli-new-project.png)
    - 决定手动选择特性，在操作提示的最后你可以选择将已选项保存为一个将来可复用的 preset。
    - 被保存的 preset 将会存在用户的 home 目录下一个名为 `.vuerc` 的 JSON 文件里。如果你想要修改被保存的 preset / 选项，可以编辑这个文件。

- 选择`Manually select features(手动安装)`则会进入[下一步选项](https://copyfuture.com/blogs-details/20200519144521753sqo6c6n1o1lx3jb)

    ```bash
    ? Please pick a preset: Manually select features
    ? Check the features needed for your project: (Press <space> to select, <a> to toggle all, <i> to invert selection)
    >( ) Babel // 代码编译
    ( ) TypeScript // ts
    ( ) Progressive Web App (PWA) Support // 支持渐进式网页应用程序
    ( ) Router // vue路由
    ( ) Vuex // 状态管理模式
    ( ) CSS Pre-processors // css预处理
    ( ) Linter / Formatter // 代码风格、格式校验
    ( ) Unit Testing // 单元测试
    ( ) E2E Testing // 端对端测试
    ```

    一般项目开发只需要选择`Babel`、`Router`、`Vuex`就足够了

    一路回车

- 安装成功

- 启动

    > ```sh
    > ＄npm run serve
    > ```

##### 4.1.3 - 项目结构分析

#### 4.2 - Vite

[Vite](https://github.com/vitejs/vite)是一个 web 开发构建工具，由于其原生 ES 模块导入方式，可以实现闪电般的冷服务器启动。

##### 4.2.1 - 创建 vite 项目

通过在终端中运行以下命令，可以使用 Vite 快速构建 Vue 项目。

- 使用 npm

    ```sh
    $ npm init vite-app <project-name>
    $ cd <project-name>
    $ npm install
    $ npm run dev
    ```

- 使用 yarn

    ```sh
    $ yarn create vite-app <project-name>
    $ cd <project-name>
    $ yarn
    $ yarn dev
    ```

##### 4.2.2 - 项目结构分析

|  目录/文件   |                   说明                   |
| :----------: | :--------------------------------------: |
| node_modules |          npm 加载的项目依赖模块          |
|    public    |             公共静态资源目录             |
|     src      | 项目源代码目录（程序员所写代码存放目录） |
|  .gitignore  |              Git 的忽略文件              |
|  index.html  |     SPA 单页面程序中唯一的 HTML 页面     |
| package.json |            项目包管理配置文件            |

###### <span style="color: #e3371e">src</span> 目录

| src 目录下 |                             说明                             |
| :--------: | :----------------------------------------------------------: |
|   assets   | 存放项目中所有<span style="color: #e3371e">静态资源文件</span>（css、fonts、图片） |
| components | 存放项目中所有的<span style="color: #e3371e">自定义组件</span> |
|  app.vue   | 项目的<span style="color: #e3371e">根目录</span>（项目运行后所见的结构） |
| index.css  |   项目的<span style="color: #e3371e">全局样式表</span>文件   |
|  main.js   |  整个项目的<span style="color: #e3371e">打包入口文件</span>  |

#### 4.2.3 - vite 项目的运行流程

在工程化项目中，vue单纯地通过 <span style="color: #e3371e">main.js</span> 把 <span style="color: #e3371e">App.vue</span> 渲染到 <span style="color: #e3371e">index.html</span> 的指定区域中

- <span style="color: #e3371e">App.vue</span> 用来编写待渲染的<span style="color: #e3371e">模版结构</span>

    - 写在 `template` 中

- <span style="color: #e3371e">index.html</span> 中需要预留一个 <span style="color: #e3371e">el 区域</span>

- <span style="color: #e3371e">main.js</span> 把 App.vue 渲染到 index.html 所预留的区域中

    ```javascript
    // main.js 文件
    // 1.从 vue 中按需导入 createApp 函数
    // ** createApp 函数的作用，创建 vue 的 "单页面应用程序实例"
    import { createApp } from 'vue'
    // 2.导入待渲染的 App组件
    import App from './App.vue'
    import './index.css'
    
    // 3.调用 createApp() 函数，返回值是 "单页面应用程序的实例"
    //   同时把 App 组件作为参数传给 createApp() 函数 ，表示要把 App 渲染到 index.html 页面上
    //   调用实例的 mount()，用来指定 vue 实际要控制的区域，把 app 组件的模版结构渲染到指定 el 区域
    createApp(App).mount('#app')
    ```

    

## 二、vue简介

### 1 - vue简介

- vue 是一套用于**构建用户界面**的**渐进式框架**。
    - 构建用户界面
        - 指令：用于辅助开发者渲染页面的模版语法
        - 数据驱动视图：数据源变化，页面结构自动重新渲染
        - 美化样式：基础CSS样式
        - 事件绑定：用于处理用户和网页之间的交互行为
    - 前端框架
        - 构建用户界面的一整套处理方案(vue 全家桶): vue(核心库) + vue-router(路由方案) + vuex(状态管理方案) + vue组件库(快速搭建页面UI效果)
        - 提供了辅助项目开发的配套工具：vue/cli + vue-devtools
            - vue/cli（npm 全局包：一键生成工程化的 vue 项目- 基于 webpack、<span style="color: teal">大而全</span>）
            - vite （npm 全局包：一键生成工程化的 vue 项目 - <span style="color: teal">小而巧</span>）
            - vue-devtools（浏览器插件：辅助调试的工具）
            - vetur（vscode 插件：提供语法高亮和智能提示）

### 2 - vue特性

#### 2.1 - 数据驱动视图

vue会监听数据的变化，数据变化时，自动重新渲染页面的结构

![](vue3.assets/01数据驱动视图.png)

- 好处：当页面数据变化时，页面会自动重新渲染
- 注意：数据驱动视图是单向的数据绑定

#### 2.2 - 双向数据绑定

<span style="color: #e3371e">填写表单</span>时，双向数据绑定可以辅助开发者在<span style="color: #e3371e">不操作 DOM </span>的前提下，<span style="color: #e3371e">自动</span>地把用户填写的内容<span style="color: #e3371e">同步</span>到数据源中

![](vue3.assets/02双向数据绑定.png) ![](vue3.assets/02双向数据绑定-2.png)

- 好处：开发者不再需要手动操作 DOM 元素，赖获取表单元素最新的值

#### 2.3 MVVM

<span style="color: #e3371e">MVVM</span> 是 vue 实现<span style="color: #e3371e">数据驱动视图</span>和<span style="color: #e3371e">双向数据绑定</span>的核心原理。

它把每个 HTML 页面都拆分成如下三部分

- <span style="color: #e3371e">M</span>odel		  表示当前页面渲染时所依赖的数据源
- <span style="color: #e3371e">V</span>iew             表示当前页面所渲染的 DOM 结构
- <span style="color: #e3371e">V</span>iew<span style="color: #e3371e">M</span>odel   连接View视图和数据源，表示 vue 的实例，是 MVVM 的核心
    - Model 数据源发生变化时，自动更新页面结构
    - 页面结构表单数据项发送变化时，自动更新值至 Model 中

##### 2.3.1 - MVVM 示意图

![](vue3.assets/03MVVM.png)

##### 2.3.2 - MVVM 工作原理

<span style="color: #e3371e">ViewModel</span> 作为 <span style="color: #e3371e">MVVM 的核心</span>，把当前页面的<span style="color: #e3371e">数据源</span>（Model）和<span style="color: #e3371e">页面的结构</span>（View）连接到一起

![](vue3.assets/03MVVM-2.png)

### 3 - vue 的基本使用

#### 3.1 - 基本使用步骤

- 导入 vue.js 的 JavaScript 脚本文件

    ```html
    <script src="https://unpkg.com/vue@next"></script>
    ```

- 在页面中声明一个将要被 vue 所控制的 DOM 区域

    ```html
    <div id="App">
      {{ username }}
    </div>
    ```

- 调用 createApp( )传入app组件返回一个应用实例

- 调用实例的 mount( )挂载应用，将 app组件 渲染到将要被 vue 所控制的 DOM 区域

    ```vue
      <script>
        const app = {
          data() {
            return {
              username: 'coco'
            }
          }
        }
    
        Vue.createApp(app).mount('#App')
      </script>
    ```

    整体

    ```html
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="utf-8">
    <title>Vue 测试实例</title>
    <script src="https://unpkg.com/vue@next"></script>
    </head>
    <body>
    <div id="App">
      {{ username }}
    </div>
    
    <script>
    const app = {
      data() {
        return {
          username: 'coco'
        }
      }
    }
    
    Vue.createApp(app).mount('#App')
    </script>
    </body>
    </html>
    ```

#### 3.2 - 基本代码与 MVVM 的对应关系

![](vue3.assets/04代码与MVVM对应关系.png)

### 4 - 安装并使用 vue-devtools

<span style="color: #0099dd">安装</span>

- 下载[igg助手](https://chrome.zzzmh.cn/info?token=ncldcbhpeplkfijdhnoepdgdnmjkckij)插件

- 开发者模式安装插件
- 搜索 vue 安装
    - bete 是 vue3

<span style="color: #0099dd">使用</span>

- F12

- 切换到 vue 选项卡

    

## 三、模版语法

项目中产生的数据通常都是会变化的，前端接收后端数据并进行处理即模板语法

### 1 - 指令

- <span style="color: #e3371e">指令</span>（Directives）是 vue 为开发者提供的<span style="color: #e3371e">模版语法</span>用于<span style="color: #e3371e">辅助开发者渲染页面的基本结构</span>

- 指令 (Directives) 是带有 `v-` 前缀的特殊 attribute

- 指令在 vue 开发中最基本、最常用、最简单

- 按<span style="color: #e3371e">用途</span>分为
    - <span style="color: #e3371e">内容渲染</span>指令
    
    - <span style="color: #e3371e">属性绑定</span>指令
    
    - <span style="color: #e3371e">事件绑定</span>指令
    
    - <span style="color: #e3371e">双向绑定</span>指令
    
    - <span style="color: #e3371e">条件绑定</span>指令
    
    - <span style="color: #e3371e">列表绑定</span>指令
    
        |     指令      |               语法               |                 作用                 |
        | :-----------: | :------------------------------: | :----------------------------------: |
        |    v-text     |        v-text="<变量名>"         |    渲染元素文本内容（覆盖默认值）    |
        |     {{ }}     |   <p>{{ 待渲染文本内容 }}</p>    |   渲染元素文本内容（不覆盖默认值）   |
        |    v-html     |        v-html="<变量名>"         |  渲染元素文本内容（包含 html 标签）  |
        | v-bind <or> : |    v-bind:<属性名>="<变量名>"    |       为元素属性动态绑定属性值       |
        |  v-on<or> @   |  v-on:<事件名>="<事件处理函数>"  |          为元素绑定事件监听          |
        |    v-model    |        v-model="<变量名>"        |        不操作DOM获取表单数据         |
        |     v-if      |          v-if=<boolean>          |         按需控制DOM显示隐藏          |
        |    v-else     |                                  |              配合 v-if               |
        |   v-else-if   |                                  |              配合 v-if               |
        |    v-show     |         v-show=<boolean>         |               <变量名>               |
        |     v-for     | v-for="(item, [index]) in items" | 基于一个数组来循环渲染相似的 UI 结构 |

#### 1.0 - 使用 JavaScript 表达式

在 vue 提供的模版渲染语法中，除了支持绑定简单的数据值之外，还支持 JavaScript 表达式的运算

```html
        <!-- 使用插值表达式期间，进行数字运算 -->
        <p>{{ number + 1 }}</p>
        <!-- 使用插值表达式期间，使用三元运算符 -->
        <p>{{ ok?'YES' : 'No' }}</p>
        <!-- 使用插值表达式期间，调用字符串的方法 -->
        <p>{{ message.split('').reverse().join('') }}</p>
        <!-- 使用 v-bind 属性绑定期间，动态进行字符串的拼接 -->
        <p :id="'list-' + id"></p>
```

#### 1.1 - 内容渲染指令

<span style="color: #e3371e">内容渲染</span>指令用于<span style="color: #e3371e">辅助开发者渲染</span><span style="color: #0099dd"> DOM 元素的文本内容</span>

##### 1.1.1 * <span style="color: #ab04d9">v-text</span>

- v-text 指令会<span style="color: teal">覆盖元素内默认的值</span>

    ```html
        <div id="App">
            <p v-text="username"></p>
            <!-- 默认文本 “性别” 会被 gender 的值覆盖掉 -->
            <p v-text="gender">性别</p>
        </div>
        <script>
            const app = {
                data() {
                    return {
                        username: 'coco',
                        gender: '女'
                    }
                }
            }
    
            Vue.createApp(app).mount('#App')
        </script>
    ```

    ```javascript
    // 页面输出
    coco
    女
    ```

##### 1.1.2 * <span style="color: #ab04d9">{{ }}</span>

- 专业名称：<span style="color: #e3371e">插值表达式（Mustache）</span>

- <span style="color: teal">不会覆盖默认文本内容</span>，开发中更常用

    ```html
        <div id="App">
            <p>姓名：{{username}}</p>
            <p>性别：{{gender}}</p>
        </div>
        <script>
            const app = {
                data() {
                    return {
                        username: 'coco',
                        gender: '女'
                    }
                }
            }
    
            Vue.createApp(app).mount('#App')
        </script>
    ```

    ```javascript
    // 页面输出
    姓名：coco
    性别：女
    ```

##### 1.1.3 * <span style="color: #ab04d9">v-html</span>

- 可以把<span style="color: teal">包含 HTML 标签的字符串渲染</span>为页面的 HTML 元素

    ```html
        <div id="App">
            <p v-text="sing"></p>
            <p>{{sing}}</p>
            <p v-html="sing"></p>
        </div>
        <script>
            const app = {
                data() {
                    return {
                        username: 'coco',
                        gender: '女',
                        sing: '<span style="color: tomato;">I can singing a song!</span>'
                    }
                }
            }
    
            Vue.createApp(app).mount('#App')
        </script>
    ```

    ![](vue3.assets/05-v-html.png)

    

#### 1.2 - 属性绑定指令

<span style="color: #e3371e">属性绑定</span>指令用于为<span style="color: #e3371e">元素的属性</span><span style="color: #0099dd"> 动态绑定属性值 </span>

##### 1.2.1 * <span style="color: #ab04d9">v-bind</span>

- 由于使用频率高，官方为其提供了<span style="color: #e3371e">简写形式</span>（英文的 <span style="color: #e3371e">:</span>）
- 特殊：对于布尔 attribute (只要存在就意味着值为 `true`)

```html
    <div id="App">
        <input type="text" v-bind:placeholder="imputValue">
        <input :type="imputType" :value="imputDefault">
        <img v-bind:src="imgSrc" alt="">
    </div>
    <script>
        const app = {
            data() {
                return {
                    imputValue: '请输入内容',
                    imputType: 'password',
                    imputDefault: '123456',
                    imgSrc: 'https://www.javascriptc.com/vue3js/logo.png'
                }
            }
        }

        Vue.createApp(app).mount('#App')
    </script>
```

#### 1.3 - 事件绑定指令

<span style="color: #e3371e">事件绑定</span>指令用于为<span style="color: #e3371e"> DOM 元素</span><span style="color: #0099dd"> 绑定事件监听 </span>

##### 1.3.1 * <span style="color: #ab04d9">v-on</span>

- 语法格式 `v-on:<事件名称>="<事件处理函数>"`

- 由于使用频率高，官方为其提供了<span style="color: #e3371e">简写形式</span>（<span style="color: #e3371e">@</span><事件名称>="<事件处理函数>）

    ```html
    <button @click="addCount">+ 1</button>
    ```

- 事件处理函数仅有一条简单语句时可<span style="color: #e3371e">省略</span>在 methods 节点中进行声明，直接写在 v-on 指令中

    ```html
    <button @click="count++">+ 1</button>
    ```

- 原生 DOM 对象有 <span style="color: teal">onclick、oninput、onkeyup</span> 等原生事件，替换为 vue 的事件绑定形式后，分别为 <span style="color: #e3371e">v-on:click、v-on:input、v-on:keyup</span>

- 通过 v-on 绑定的事件处理函数，需要在 <span style="color: #e3371e">methods 节点</span>中进行声明

    ```html
        <div id="app">
            <p>{{ count }}</p>
            <button v-on:click="addCount">+ 1</button>
        </div>
    
        <script>
            const app = {
                data() {
                    return {
                        count: 0
                    }
                },
                methods: {
                   addCount() {
                       this.count += 1
                   } 
                }
            }
            Vue.createApp(app).mount('#app')
        </script>
    ```

##### 1.3.2 * 事件传参

- 在使用 v-on 指令绑定事件时，可以使用 ( ) 进行传参

    ```html
        <div id="app">
            <p>{{ count }}</p>
            <button @click="addCount(step)">+ 1</button>
        </div>
    
        <script>
            const app = {
                data() {
                    return {
                        count: 0
                    }
                },
                methods: {
                    addCount(step) {
                        this.count += e
                    }
                }
            }
            Vue.createApp(app).mount('#app')
        </script>
    ```

##### 1.3.3 * 事件对象

- 在原生的 DOM 事件绑定中，可以在事件处理函数形参处，接收事件对象 event

- 同理，在 v-on 指令中（简写为@）所绑定的事件处理函数中，同样可以接收到事件对象 event

    ```html
        <div id="app">
            <p>{{ count }}</p>
            <button @click="addCount">+ 1</button>
        </div>
    
        <script>
            const app = {
                data() {
                    return {
                        count: 0
                    }
                },
                methods: {
                    addCount(e) {
                        this.count += 1;
                        // 声明变量 nowBgColor 接收按钮背景色
                        const nowBgColor = e.target.style.background;
                        // 三元表达式判断背景色并赋值给按钮背景色样式
                    e.target.style.background = nowBgColor === ''? 'red' : '';
                    }
            }
            }
            Vue.createApp(app).mount('#app')
    	</script>
    ```

##### 1.3.4 * $event

- <span style="color: #e3371e">$event</span> 是 vue 提供的特殊变量，用来表示<span style="color: teal">原生的事件参数对象 event</span>

- $event 可以解决事件参数对象 event 被覆盖的问题

    ```html
        <div id="app">
            <p>{{ count }}</p>
            <button @click="addCount(2, $event)">+ 1</button>
        </div>
    
        <script>
            const app = {
                data() {
                    return {
                        count: 0
                    }
                },
                methods: {
                    addCount(step, e) {
                        this.count += step;
                        const bgc = e.target.style.background;
                        e.target.style.background = bgc == '' ? 'pink' : '';
                    }
                }
            }
            Vue.createApp(app).mount('#app')
        </script>
    ```

##### 1.3.5 * 事件修饰符（modifier）

- 事件处理函数中调用 <span style="color: #e3371e">preventDefault( )</span> 或 <span style="color: #e3371e">stopPropagation( )</span> 是非常常见的需求

- 因此， vue 中提供了事件修饰符的概念，<span style="color: #e3371e">方便</span>对事件的触发进行控制

- 常见的 5 个修饰符：

    |                  事件修饰符                  |                             说明                             |
    | :------------------------------------------: | :----------------------------------------------------------: |
    | <span style="color: #e3371e">.prevent</span> | <span style="color: #e3371e">阻止默认行为</span>（如：阻止 a 链接的跳转、表单提交） |
    |  <span style="color: #e3371e">.stop</span>   |       <span style="color: #e3371e">阻止事件冒泡</span>       |
    |                   .capture                   |               以捕获模式触发当前的事件处理函数               |
    |                    .once                     |                     绑定的事件只触发一次                     |
    |                    .self                     |     只有在 event.target 是当前元素自身时触发事件处理函数     |

    ```html
            <!-- 阻止链接跳转 -->
            <a href="https://www.taobao.com/" @click.prevent="onLinkClick">淘宝</a>
            <h4>.stop</h4>
            
    
            <div id="outer" @click="onOuterClick">
                <div id="middle" @click="onMiddleClick">
                    <!-- 阻止冒泡 -->
                    <div id="inner" @click.stop="onInnerClick"></div>
                </div>
            </div>
    		
    		<!-- 以捕获模式触发当前的事件处理函数 -->
            <div id="outer" @click.capture="onOuterClick">
                <div id="middle" @click="onMiddleClick">
                    <div id="inner" @click="onInnerClick"></div>
                </div>
            </div>
    
            <div id="outer" @click.capture="onOuterClick">
                <!-- 只有在 event.target 是当前元素自身时触发事件处理函数 -->
                <div id="middle" @click.self="onMiddleClick">
                    <div id="inner" @click="onInnerClick"></div>
                </div>
            </div>		
    ```

##### 1.3.6 * 按键修饰符

- 在监听<span style="color: #e3371e">键盘事件</span>时，经常需要判断详细的按键，此时，可为<span style="color: #e3371e">键盘相关事件</span>添加<span style="color: #0099dd">按键修饰符</span>

- 按键修饰符只能配合键盘事件触发

    ```html
        <div id="App">
            <input type="text" @keyup.enter="submit" @keydown.esc="clearInput">
    </div>
    
        <script>
            // 按下并松开 enter 输出文本内容；按下 esc 清空文本内容
            const app = {
                data () {
                    return {
    
                    }
                },
                methods: {
                    submit (e) {
                        console.log('你输入的内容是:' + e.target.value);
                    },
                    clearInput(e) {
                        e.target.value = ''
                    }
                }
            }
            
            Vue.createApp(app).mount("#App")
        </script>
    ```

#### 1.4 - 双向绑定指令

<span style="color: #e3371e">双向绑定</span>指令用于为<span style="color: #e3371e"> 不操作DOM 元素</span>的前提下<span style="color: #0099dd"> 快速获取表单的数据 </span>

`v-model` 在内部为不同的输入元素使用不同的 property 并抛出不同的事件

- text 和 textarea 元素使用 `value` property 和 `input` 事件；
- checkbox 和 radio 使用 `checked` property 和 `change` 事件；
- select 字段将 `value` 作为 prop 并将 `change` 作为事件。

##### 1.4.1 * <span style="color: #ab04d9">v-model</span>

- v-model <span style="color: #e3371e">只能配合表单元素</span>一起使用

    ```html
        <div id="app">
            <p>用户名：{{ username }}</p>
            <input type="text" v-model="username">
            <section>
                <p>您的省份是：{{ province }}</p>
                <select v-model="province">
                    <option value="0">请选择</option>
                    <option value="1">北京</option>
                    <option value="2">上海</option>
                    <option value="3">广东</option>
                </select>
            </section>
        </div>
    
        <script>
            const app = {
                name: 'myApp',
                data() {
                    return {
                        username: '',
                        province: '2'
                    }
                }
            }
    
            Vue.createApp(app).mount('#app')
        </script>
    ```

##### 1.4.2 * v-model指令的修饰符

- 为方便对用户输入内容处理，vue 为 v-model 提供了 3 个修饰符

    | 修饰符  |                作用                 |                    示例                     |
    | :-----: | :---------------------------------: | :-----------------------------------------: |
    | .number |    自动将用户输入值转为数值类型     | <input type="text" v-model.trim="username"> |
    |  .trim  |   自动过滤用户输入的首尾空白字符    |  <input type="text" v-model.number="age">   |
    |  .lazy  | 在“change”时更新，而非“input”时更新 | <input type="text" v-model.lazy="address">  |

#### 1.5 - 条件渲染指令

<span style="color: #e3371e">条件渲染</span>指令用于<span style="color: #0099dd"> 按需控制 DOM 的显示与隐藏</span>

##### 1.5.1 * <span style="color: #ab04d9">v-if</span>

- 语法：`v-if=<boolean>`  。为<span style="color: #e3371e"> true </span>时<span style="color: #e3371e">显示元素</span>，为<span style="color: #0099dd">false</span>时<span style="color: #0099dd">隐藏元素 </span>

##### 1.5.2 * <span style="color: #ab04d9">v-show</span>

- 效果与 v-if 一样

```html
    <div id="app">
        <!-- 点击按钮切换 flag -->
        <button @click="flag = !flag">toggle Flag</button>
        <p v-if="flag">请求成功 —— 被 v-if 控制</p>
        <p v-show="flag">请求成功 —— 被 v-show 控制</p>
    </div>

    <script>
        const app = {
            name: 'myApp',
            data() {
                return {
                    // flag 用以控制元素的显示与隐藏
                    // 为 ture 时显示元素，为 false 时隐藏元素
                    flag: true
                }
            }
        }

        Vue.createApp(app).mount('#app')
    </script>
```

##### 1.5.3 * v-if 与 v-show 的区别

- 实现原理不同：
    - <span style="color: #e3371e">v-if</span> 指令会<span style="color: #e3371e">动态地创建或移除 DOM 元素</span>，从而控制元素在页面上的显示与隐藏
    - <span style="color: #0099dd">v-show</span> 指令会<span style="color: #0099dd">动态地添加或移除 style="display:none" 样式</span>，从而控制元素的显示与隐藏
- 性能消耗不同：
    - <span style="color: #e3371e">v-if</span>有更高的<span style="color: #e3371e">切换开销</span>
    - <span style="color: #0099dd">v-show</span>有更高的<span style="color: #0099dd">初始渲染花销</span>
- 应用
    - <span style="color: #e3371e">运行时条件很少改变</span>，使用<span style="color: #e3371e"> v-if </span>更好
    - 需要<span style="color: #0099dd">非常频繁地切换</span>，使用<span style="color: #0099dd">v-show</span>更好

##### 1.5.4 * v-else （配合 v-if 使用）

v-if 可以单独使用，或配合 v-else 一起使用

```html
    <div id="app">
        <p v-if="num < 5">随机数 小于 5</p>
        <p v-else>随机数 大于 5</p>
    </div>

    <script>
        const app = {
            name: 'myApp',
            data() {
                return {
                    num: Math.random() * 10
                }
            }
        }

        Vue.createApp(app).mount('#app')
    </script>
```

##### 1.5.5 * v-else-if

v-else-if 指令，充当 v-if 的 “ else-if ”块，可以连续使用

```html
    <div id="app">
        <p v-if="score > 90">优秀</p>
        <p v-else-if="score > 80">良好</p>
        <p v-else-if="score > 60">及格</p>
        <p v-else>不及格！</p>
    </div>

    <script>
        const app = {
            name: 'myApp',
            data() {
                return {
                    score: Math.random() * 100
                }
            }
        }

        Vue.createApp(app).mount('#app')
    </script>
```

#### 1.6 - 列表渲染指令

<span style="color: #e3371e">列表渲染</span>指令用于<span style="color: #0099dd"> 基于一个数组来循环渲染相似的 UI 结构</span>

##### 1.6.1 * <span style="color: #ab04d9">v-for</span>

- v-for 指令需要使用 <span style="color: #e3371e">item in items</span> 的特殊语法
    - items 是 <span style="color: teal">带循环的数组</span>
    - item 是 <span style="color: teal">当前循环项</span>

```html
    <div id="app">
        <ul>
            <li v-for="user in list">姓名是：{{ user.username }}</li>
        </ul>
    </div>

    <script>
        const app = {
            name: 'myApp',
            data() {
                return {
                    list: [
                        { id: 1 , username: '阿猫'},
                        { id: 2 , username: '阿狗'},
                        { id: 3 , username: '阿猪'}
                    ]
                }
            }
        }

        Vue.createApp(app).mount('#app')
    </script>
```

- v-for 指令还支持一个<span style="color: #e3371e">可选</span>的第二个参数，为当前项的<span style="color: #e3371e">索引</span>
    - 语法格式： `(item, inex) in itesm`
    - v-for 指令中的 <span style="color: #0099dd">item</span> 项 和 <span style="color: #0099dd">index</span> 索引都是<span style="color: #0099dd">形参</span>，可根据需要<span style="color: #0099dd">重命名</span>

```html
<li v-for="(user, index) in list">索引是：{{ index }} ,姓名是：{{ user.username }}</li>
```

##### 1.6.2 * 使用 key 维护列表的状态

- <span style="color: #e3371e">列表数据变化</span>时，<span style="color: #e3371e">默认情况</span>下，<span style="color: #e3371e">vue</span> 会<span style="color: #e3371e">尽可能的复用</span>已经存在的 DOM 元素，从而<span style="color: #e3371e">提升渲染的性能</span>
- 但这种默认的性能优化策略，会导致<span style="color: #0099dd">有状态的列表无法被正确更新</span>
- 为给 vue 一个提示，以便它跟踪每个节点的身份，从而保证<span style="color: #e3371e">有状态的列表被正确更新</span>的前提下，<span style="color: #e3371e">提升渲染的性能</span>。此时，需要为每项提供一个<span style="color: #ab04d9">唯一的 key 属性</span>

```vue
<!-- 用户列表区域 -->
<ul>
    <!-- 加 key 属性的好处： -->
    <!-- 1. 正确维护列表的状态 -->
    <!-- 2. 复用现有的 DOM 元素，提升渲染的性能 -->
    <li v-for="user in userlist" :key="user.id">
        <input type="checkbox">
        姓名：{{user.name}}
    </li>
</ul>
```

- key 的注意事项
    - key 的值只能是 string 或 number 类型
    - key 的值必须具有唯一性（不能重复）
    - 建议使用数据项 id 属性的值作为 key 的值 （id 属性的值具有唯一性）
    - 使用 index 的值当做 key 的值没有任何意义（index 的值不具有唯一性，会随数据变化动态更新）
    - 建议使用 v-for 指令时一定要指定 key 的值（技能提升性能，有防止列表状态紊乱）

#### 案例：品牌列表

##### 知识点

- bootstrap 4.x 相关：
    - 卡片（card）、表单相关（forms）、按钮（buttons）、表格（tables）
- vue指令与过滤器相关：
    - 插值表达式、属性绑定、事件绑定、双向数据绑定、修饰符、条件渲染、列表渲染、全局过滤器

##### 步骤

- 创建基本的 vue 实例

    - 导入 vue （js文件、cdn……）
    - 创建应用实例
    - 添加数据源 [品牌列表数据]

- 基于 vue 渲染表格数据

    - 使用 v-for 指令渲染表格数据，同时添加key动态绑定当前项的 id 值

    - 利用 bootstrap 将品牌的状态 state 渲染为 switch 开关效果

        switch开关效果：https://v4.bootcss.com/docs/components/forms/#switches

    - 用计算属性或方法代替过滤器，添加方法对日期格式化

- 实现添加品牌功能

    - 阻止表单默认提交行为
    - 为 input 输入框进行 v-model 双向数据绑定
        - 需要在 data 数据中声明 brandname 属性字段
    - 为 添加品牌 的 button 按钮绑定 click 事件处理函数
    - 在 data 中声明 nextId 属性（用来记录下一个可用的 id 值），并在 methods 表面 addNewBrand 事件处理函数
    - 监听 input 输入框的 keydown 事件，通过 .esc 按键修饰符快速清空文本框内容

- 实现删除品牌功能

    - 为删除的 a 链接绑定 click 点击事件处理函数，并阻止器默认行为
    - 

- 实现修改品牌状态的功能

##### 完整代码

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>品牌列表案例</title>
    <link rel="stylesheet" href="https://cdn.staticfile.org/twitter-bootstrap/4.3.1/css/bootstrap.min.css">
    <script src="https://cdn.staticfile.org/twitter-bootstrap/4.3.1/js/bootstrap.min.js"></script>
    <script src="https://unpkg.com/vue@next"></script>
    <style>
        :root {
            font-size: 13px;
        }

        body {
            padding: 8px;
        }
    </style>
</head>

<body>
    <div id="app">
        <!-- 卡片区域 -->
        <div class="card">
            <h5 class="card-header">添加品牌</h5>
            <div class="card-body">
                <!-- 添加品牌的表单 -->
                <!-- 阻止表单提交行为 -->
                <form class="form-inline" @submit.prevent>
                    <div class="input-group mb-2 mr-sm-2">
                        <div class="input-group-prepend">
                            <div class="input-group-text">品牌名称</div>
                        </div>
                        <!-- 文本输入况 -->
                        <input type="text" class="form-control" placeholder="请输入品牌名称" v-model.trim="brandname" @keydown.esc="brandname = ''">
                    </div>

                    <!-- 提交表单的按钮 -->
                    <button type="submit" class="btn btn-primary mb-2" @click="addNewBrand">添加品牌</button>
                </form>
            </div>
        </div>

        <!-- 品牌列表 -->
        <table class="table table-bordered table-striped mt-2">
            <thead>
                <tr>
                    <th>序号</th>
                    <th>品牌名称</th>
                    <th>状态</th>
                    <th>创建时间</th>
                    <th>操作</th>
                </tr>
            </thead>
            <!-- 表格的主体区域 -->
            <tbody>
                <!-- TODO: 循环渲染表格的每一行数据 -->
                <tr v-for="(item, index) in brandlist" :key="item.id">
                    <td>{{ index + 1 }}</td>
                    <td>{{ item.brandname }}</td>
                    <td>
                        <div class="custom-control custom-switch">
                            <input type="checkbox" class="custom-control-input" :id="item.id" v-model="item.state">
                            <label class="custom-control-label" :for="item.id" v-if="item.state">已启用</label>
                            <label class="custom-control-label" :for="item.id" v-else>已禁用</label>
                        </div>
                    </td>
                    <td>{{ timeFormat }}</td>
                    <td><a href="#" @click.prevent="removeBrand(item.id)">删除</a></td>
                </tr>
            </tbody>
        </table>
    </div>

    <script>
        const app = {
            data() {
                return {
                    brandname: '',
                    // 下一个可用的 Id 值
                    nextId: 4,
                    brandlist: [
                        { id: 1, brandname: '宝马', state: true, addtime: new Date() },
                        { id: 2, brandname: '奥迪', state: true, addtime: new Date() },
                        { id: 3, brandname: '奔驰', state: true, addtime: new Date() }
                    ]
                }
            },
            methods: {
                // 添加新的品牌
                addNewBrand() {
                    if (!this.brandname) {
                        return alert('品牌名称不能为空')
                    } else {
                        this.brandlist.push({
                            id: this.nextId,
                            brandname: this.brandname,
                            state: true,
                            addtime: new Date()
                        })
                        this.brandname = ''
                        this.nextId++
                    }
                },
                // 删除品牌
                removeBrand(id) {
                    this.brandlist = this.brandlist.filter(x => x.id !== id)
                }
            },
            computed: {
                // 对日期格式化
                timeFormat() {
                    const dt = new Date()
                    const y = padZero(dt.getFullYear())
                    const m = padZero(dt.getMonth() + 1)
                    const d = padZero(dt.getDate())

                    const hh = padZero(dt.getHours())
                    const mm = padZero(dt.getMinutes())
                    const ss = padZero(dt.getSeconds())

                    return `${y}-${m}-${d} ${hh}:${mm}:${ss}`
                    // 补零操作
                    function padZero(n) {
                        return n > 9 ? n : '0' + n
                    }
                }
            }
        }

        Vue.createApp(app).mount('#app')
    </script>
</body>

</html>
```



## 四、组件基础

### 1 - 单页面应用程序

单页面应用程序（Single Page Application，简称 SPA）：一个 Web 网站中只有唯一的一个 HTML 页面，所有的功能和交互都在这唯一的一个页面内完成

#### 1.1 - 特点

- 仅在该 web 页面初始化时加载相应的资源（HTML、CSS 和 JavaScript）
- 一旦页面加载完成，SPA 不会因用户操作二进行页面的重新加载和跳转，而是利用 JavaScript 动态地变化 HTML 的内容，从而实现页面与用户的交互

#### 1.2 - 优点

- <span style="color: teal">良好的交互体验</span>
    - 单页应用的内容的改变不需要重新加载整个页面
    - 获取数据也是通过 Ajax 异步获取
    - 没有页面之间的跳转，不会出现‘白屏现象’
- <span style="color: teal">良好的前后端工作分离模式</span>
    - 后端专注于提供 API 接口，更易实现 API 接口的复用
    - 前端专注于页面的渲染，更利于前端工程化的发展
- <span style="color: teal">减轻服务器的压力</span>
    - 服务器只提供数据，不负责页面的合成与逻辑的处理，吞吐能力提高几倍

#### 1.3 - 缺点

- 首屏加载慢

    解决方案

    - 路由懒加载
    - 代码压缩
    - CDN 加速
    - 网络传输压缩

- 不利于 SEO

    解决方案

    - SSR 服务器端渲染

### 2 - 快速创建 vue 的 SPA 项目

vue官方提供了<span style="color: #e3371e">两种</span>快速创建工程化的 SPA 项目的方式

- 基于 <span style="color: #e3371e">vite</span> 创建的 SPA 项目

- 基于 <span style="color: #e3371e">vue-cli</span> 创建的 SPA 项目

    |                            |     vue-cli     |        vite        |
    | :------------------------: | :-------------: | :----------------: |
    |      支持的 vue 版本       | 支持 3.x 和 2.x |   仅支持 vue3.x    |
    |      是否基于 webpack      |       是        |         否         |
    |          运行速度          |      较慢       |         快         |
    |         功能完整度         |     大而全      | 小而巧（逐渐完善） |
    | 是否建议在企业级开发中使用 |      建议       |     目前不建议     |

### 3 - 组件化开发

#### 3.1 - 思想

组件化开发：根据<span style="color: #e3371e">封装</span>的思想，<span style="color: #e3371e">把页面上可以复用的部分封装为组件</span>，从而方便项目的开发和维护

#### 3.2 - 好处

- 提高了前端代码的<span style="color: #e3371e">复用性</span>和<span style="color: #e3371e">灵活性</span>
- 提高了<span style="color: #e3371e">开发效率</span>和<span style="color: #e3371e">可维护性</span>

#### 3.3 - vue 中的组件开发

- vue 是一个<span style="color: #e3371e">完全支持组件化开发</span>的框架
- vue 中规定<span style="color: #e3371e">组件的后缀名</span>时 <span style="color: #e3371e">.vue</span> 
- 之前接触到的 app.vue 文件本质上就是一个 vue 的组件

#### 3.4 - vue 组件的构成

组件时可复用的组件实例，且带有一个名字

每个 <span style="color: teal">.vue</span> 组件 都由 3 部分构成：

- <span style="color: #e3371e">template</span>	——>	组件的<span style="color: #e3371e">模版结构</span>
- <span style="color: #e3371e">script</span>	——>	组件的<span style="color: #e3371e">JavaScript 行为</span>
- <span style="color: #e3371e">style</span>	——>	组件的<span style="color: #e3371e">样式</span>

注意：每个组件中<span style="color: #e3371e">必须包含 template</span> 模版结构，而 <span style="color: #0099dd">JavaScript 行为</span>和 <span style="color: #0099dd">style 样式</span> 是<span style="color: #0099dd">可选</span>的组成部分

##### 3.4.1 - 组件的 【 template 】 节点

- vue规定：每个组件对应的模板结构，需要定义到<template>节点中
- 注意：<template> 是 vue 提供的容器标签，只起到包裹性质的作用，不会被渲染成真正的 DOM 元素

###### 在 template 中使用指令

在组件的<template>节点中，支持前面所学的指令语法，赖辅助开发者渲染当前组件的 DOM 结构

```vue
<template>
  <h1>这是 App 根组件</h1>
  <!-- 使用 {{ }} 插值表达式 -->
  <p>生成一个随机数字：{{ ( Math.random () * 10).toFixed(2) }}</p>
  <!-- 使用 v-bind 属性绑定 -->
  <p  :title="new Date().toLocaleTimerString()">Lorem ipsum dolor sit amet.</p>
  <!-- 属性 v-on 事件绑定 -->
  <button @click="showInfo">按钮</button>
</template>
```

###### 在 template 中定义根节点

在 vue 2.x 的版本中，<template> 节点内的 DOM 结构仅支持单个根节点

```vue
<template>
  <div>
    <h1>根节点1</h1>
    <h2>根节点2</h2>
  </div>
</template>
```

在 vue 3.x 的版本中，<template> 支持<span style="color: #e3371e">定义多个根节点</span>

```vue
<template>
    <h1>根节点1</h1>
    <h2>根节点2</h2>
</template>
```



##### 3.4.2 - 组件的 【 script 】 节点

- vue规定：组件内的 <script> 节点是<span style="color: #e3371e">可选</span>的，开发者可以在 <script> 节点中封装组件的 JavaScript 业务逻辑

-  <script> 节点的基本结构如下

    ```vue
    <script>
    // 今后，组件相关的 data 数据、methods 方法等，
    // 都需要定义到 export default 所导出的对象中
    export default {
      
    }
    </script>
    ```

###### 在  script 节点中使用的节点

- name 节点

    - 可以通过 name 节点给当前组件定义一个名称

    - 使用 vue-devtools 进行项目调试的时候，自定义的组件名称可以<span style="color: #e3371e">清晰的区分每个组件</span>

        ```vue
        <script>
        export default {
          // name 属性指向的是当前组价的名称（建议：每个单词的首字母大写）
          name: 'MyApp',
        }
        </script>
        ```

- data 节点

    - <span style="color: #e3371e">vue 组件渲染期间</span>所需用到的<span style="color: #e3371e">数据</span>，可以定义在 data 节点中

    - 组件中声明 data数据，组件的 data 选项是一个函数，函数向外return一个对象

        ```vue
        <template>
          <p>我的名字是{{ username }}</p>
        </template>
        
        <script>
        export default {
          // 组件名称
          name: "MyApp",
          // 组件的数据（data方法中 return 出去的对象，就是当亲啊组件渲染期间所需用到的数据对象）
          data() {
            return {
              username: 'coco',
            };
          },
        };
        </script>
        ```

        ```
        // 页面输出：我的名字是coco
        ```

- methods 节点

    - 组件中的<span style="color: #e3371e">事件处理函数</span>，必须定义到<span style="color: #e3371e"> methods 节点</span>中

    - methods 指向一个对象，在对象中声明一个事件处理函数（函数中 this 指向当前组件的实例），

        ```vue
        <template>
          <p>count 的 值是：{{ count }}</p>
          <button @click="addCount">+ 1 </button>
        </template>
        
        <script>
        export default {
          name: "MyApp",  // 组件名称
          data() {        // 组件的数据
            return {
              count: 0,
            }
          },
          methods: {
            addCount() {
              // 通过 this 访问组件 data 内的数据
              this.count++
            }
          }
        };
        </script>
        ```

##### 3.4.3 - 组件的 【 style 】 节点

- vue 规定：组件内的 <style> 节点是<span style="color: #e3371e">可选</span>的，开发者可以在 <style> 节点中编写样式美化当前组件的 UI 结构

-  <style> 节点的基本结构如下

    - 属性 `lang="css"` 是可选的，表示所使用的样式语言。默认只支持 css 语法，可选择还有 less、scss等

    ```vue
    <style lang="css">
    h1 {
      font-weight: normal;
    }
    </style>
    ```

- 让 style 支持 less 语法

    - 安装依赖包，从而提供 less 语法的编译支持

        ```sh
        $ npm install less -D
        ```

    - 在 <style> 标签上 添加`lang="less"` 属性，即可使用 less 语法编写组件的样式

### 4 - 组件的基本使用

#### 4.1 - 组件的注册

组件之间可以进行<span style="color: #e3371e">相互的引用</span>

##### 4.1.1 - 组件使用原则

- **先注册后使用**

- 全局注册和局部注册的应用
    - 开发期间使用频率很高，全局注册
    - 只在特定情况使用，局部注册

![](vue3.assets/06-组件的引用.png)

##### 4.1.2 - 注册组件的两种方式

- <span style="color: #ab04d9">全局注册</span>

    - 被全局注册的组件，可以在全局任何一个组件内使用

    ![](vue3.assets/07-全局注册.png)

- <span style="color: #ab04d9">局部注册</span>

    - 被局部注册的组件，只能在当前注册的范围内使用

![](vue3.assets/08-局部注册.png)

##### 4.1.3 - 全局注册组件

###### Ⅰ - 步骤

- 在 <span style="color: #e3371e">main.js</span> 项目入口文件<span style="color: #e3371e">导入</span>需要被全局注册的组件

    ```javascript
    // main.js 项目入口文件
    import Swiper from './components/01.globalReg/Swiper.vue'
    ```

- 调用 app 实例的 component（）方法对组件全局注册

    ```javascript
    // main.js 项目入口文件
    app.component('my-swiper',Swiper)
    ```

    - component（）方法接收两个参数

        - 第一个参数：全局注册完毕后，<span style="color: #e3371e">组件的名称</span>

        - 第二个参数：<span style="color: #e3371e">要注册的组件</span>
        
            - 在 components 文件夹下新建并编辑

                ```vue
        // components/01.globalReg/Swiper.vue 文件
                <template>
                ```
            <h3>Swiper 轮播图组件</h3>
                </template>
                
                <script>
                export default {
                    name: 'MySwiper'
                }
                </script>
                ```
    
- 注册完毕后，在 App.vue 中<span style="color: #e3371e">直接以标签的形式进行使用</span>

    ```vue
    <template>
      <my-swiper></my-swiper>
      <my-test></my-test>
    </template>
    ```

###### Ⅱ - 完整代码

```vue
// Swiper.vue 文件
<template>
    <h3>Swiper 轮播图组件</h3>
</template>

<script>
export default {
    name: 'MySwiper' // 组件名字
}
</script>
```

```javascript
// main.js 文件
import { createApp } from 'vue';
import App from './App.vue';

// 1.导入 Swiper 组件
import Swiper from './components/01.globalReg/Swiper.vue'

const app = createApp(App);

// 2.调用 app 实例的 component()，在全局注册 my-swiper 组件
app.component('my-swiper',Swiper)

app.mount('#app');
```

```vue
// App.vue 文件
<template>
  <my-swiper></my-swiper>
  <my-test></my-test>
</template>

<script>
export default {
  name: "MyApp",  // 组件名称
  data() {        // 组件的数据
    return {
      count: 0,
    }
  },
  methods: {
    addCount() {
      // 通过 this 访问组件 data 内的数据
      this.count++
    }
  }
};
</script>
```

##### 4.1.4 - 局部注册组件

###### Ⅰ - 步骤

- 在 父组件 文件<span style="color: #e3371e">导入</span>需要被局部注册的组件

    ```vue
    // App.vue 文件
    <script>
    // 导入子组件
    import Search from './components/02.privateReg/Search.vue'
    
    <code>
    </script>
    ```

- 在父组件 `export default` 中，通过 <span style="color: #e3371e">components</span> 节点，为当前组件注册私有子组件

    ```vue
    <script>
    export default {
      name: "MyApp", // 组件名称
      data() {
      },
      methods: {
      },
      components: {
        'my-search': Search  // 注册子组件
      }
    };
    </script>
    ```

    - 注册期间，以键值对形式为子组件指定 <span style="color: #0099dd">自定义组件的名字 </span>和 <span style="color: #0099dd">待注册子组件</span>

- 注册完毕后，在 App.vue 中<span style="color: #e3371e">直接以标签的形式进行使用</span>

    ```vue
    <template>
      <my-search></my-search>
    </template>
    ```

###### Ⅱ - 完整代码

```vue
// Search.vue 文件
<template>
    <h4>这是 Search 子组件</h4>
</template>

<script>
export default {
    name: 'MySearch'
}
</script>
```

```vue
// App.vue 文件
<template>
  <my-search></my-search>
</template>

<script>
// 导入子组件
import Search from './components/02.privateReg/Search.vue'

export default {
  name: "MyApp", // 组件名称
  data() {
    // 组件的数据
    return {
      count: 0,
    };
  },
  methods: {
    addCount() {
      // 通过 this 访问组件 data 内的数据
      this.count++;
    },
  },
  components: {
    'my-search': Search
  }
};
</script>

<style lang="less">
h1 {
  font-weight: normal;
  color: red;
  strong {
    color: teal;
  }
}
</style>
```

##### 4.1.5 - 组件注册时名称的大小写

在进行组件的注册时，定义组件注册名称的方式有两种

- Kebab-case 命名法（俗称<span style="color: #e3371e">短横线命名法</span>，例 my-search）
    - 字母全<span style="color: #ffa1d4">小写</span>，包含<span style="color: #ffa1d4">连字符</span>（多个单词与连字符符号连接）
    - 必须严格按照短横线名称使用
- PascalCase 命名法（俗称<span style="color: #e3371e">帕斯卡命名法</span>或<span style="color: #e3371e">大驼峰命名法</span>，例 MySearch） <span style="color: #ab04d9">推荐使用</span>
    - 既可严格按照帕斯卡名称使用
    - 又可以<span style="color: #0099dd">转化为短横线名称</span>使用

##### 4.1.6 - 通过 name 属性注册组件

注册组件期间

- 可以直接提供组件的注册名称
- 也可把组件的 <span style="color: #e3371e">name 属性</span>作为注册后组件的组件名称

```vue
// Swiper 组件
<template>
    <h3>Swiper 轮播图组件</h3>
</template>

<script>
export default {
    name: 'MySwiper'
}
</script>
```

```javascript
// main.js 项目入口文件
app.component(Swiper.name,Swiper)	// 相当于app.component('MySwiper',Swiper)
```

#### 4.2 - 父子组件之间的样式冲突

##### 4.2.1 - 原因

默认情况，写在 <span style="color: #e3371e">.vue  组件中的样式</span>会<span style="color: #e3371e">全局生效</span>，因此容易造成多个组件之间的样式冲突问题。

根本原因是：

- 单页面应用程序中，<span style="color: #0099dd">所有组件的 DOM 结构</span>，都是<span style="color: #0099dd">基于唯一的 index.html 页面</span>进行呈现的
- 每个组件中的样式，都会<span style="color: #0099dd">影响整个 index.html 页面</span>中的 DOM 元素

##### 4.2.2 - 解决

- 方法 1 （较麻烦）
    - 为每个组件手动分配唯一的自定义属性

        ```vue
        <h3 data-v-app>App 根组件</h3>
        ```

    - 编写组件样式时，通过属性选择器来控制样式的作用域

        ```vue
        <style lang="less">
        p[data-v-app] {
          color: red;
        }
        </style>
        ```

- 方法 2 —— <span style="color: #ab04d9">style 节点的 scoped 属性</span>

    - vue 为 style节点提供了 <span style="color: #ffa1d4">scoped 属性</span>，从而防止 组件之间的样式冲突 问题

    - 加上 scoped 属性后，vue 会<span style="color: #ab04d9">自动</span>为当前组件分配唯一的“<span style="color: #ab04d9">自定义属性</span>”

        ```html
        <h3 data-v-7bc0fb25="">App 根组件</h3>
        ```

##### 4.2.3 - :deep( ) 样式穿透

给当前组件的 style 节点添加了 scoped 属性：

- 则当<span style="color: #e3371e">前组件的样式对其子组件时不生效</span>的

- 使用<span style="color: #e3371e"> :deep( )深度选择器</span>，可使某些样式<span style="color: #e3371e">对子组件生效</span>

    ```vue
    // 父组件 App.vue 中
    <style lang="less" scoped>
    :deep(.tittle) {		// 子组件中 tittle 类的元素也会收到影响
        color: red;
    }
    </style>
    ```

### 5 - 组件的 props

#### 5.1 - 组件封装时的基本原则

为提高组件的<span style="color: #e3371e">复用性</span>，封装 vue 组件时需要遵守如下的原则：

- 组件的<span style="color: #e3371e"> DOM 结构、Style 样式</span>要尽量复用
- 组件中<span style="color: #e3371e">要展示的数据</span>，尽量由组件的使用者提供

为方便<span style="color: #e3371e">使用者</span>为组件<span style="color: #0099dd">提供</span>要<span style="color: #0099dd">展示的数据</span>，vue 组件提供了 <span style="color: #0099dd">props</span> 的概念

#### 5.2 - 组件的 props 介绍

props 是组件的<span style="color: #e3371e">自定义属性</span>，组件的使用者可以<span style="color: #e3371e">通过 props 把数据传递到子组件的内部</span>，供子组件内部进行使用

- props 的<span style="color: #0099dd">作用</span>：父组件在使用子组件时，通过 props <span style="color: #0099dd">向子组件传递要展示的数据</span>
- props 的<span style="color: #0099dd">好处</span>：提高了组件的 <span style="color: #0099dd">复用性</span>

#### 5.3 - 封装组件时声明 props

- 在封装 vue 组件时，可以把<span style="color: #e3371e">动态的数据项</span>声明为 <span style="color: #e3371e">props </span>自定义属性
- 自定义属性可以在当前组件的模板结构中被直接使用

```vue
// MyArticle.vue 子组件
<template>
    <h3>标题：{{ tittle }}</h3>
    <h3>作者：{{ author }}</h3>
</template>

<script>
export default {
    name: 'MyArticle',
    // 外界可以传递指定的数据，到当前的组件中
    props: ['tittle', 'author']
}
</script>
```

```vue
// App.vue 父组件
<template>
    <h3>App root</h3>
    <my-article title="我的区长父亲" author="袁华"></my-article>
</template>

<script>
import MyArticle from './MyArticle.vue'

export default {
    name: 'MyApp',
    components: {
        MyArticle  // 注册组件时简写 'MyArticle':MyArticle
    }
}
</script>
```

#### 5.4 - 无法使用未声明的 props

```vue
<my-article title="致橡树" author="舒婷"></my-article>

<template>
    <h3>标题：{{ tittle }}</h3>
    <h3>作者：{{ author }}</h3>
</template>

<script>
export default {
    name: 'MyArticle',
    // author 属性没有声明，因此子组件无法访问到 author 值
    props: ['tittle']
}
</script>
```

#### 5.5 - 动态绑定 props 的值

可以使用 <span style="color: #e3371e">v-bind 属性绑定的形式</span>，为组件动态绑定 props 的值

```vue
// MyArticle 子组件
<template>
    <h3>标题：{{ tittle }}</h3>
    <h3>作者：{{ author }}</h3>
</template>

<script>
export default {
    name: 'MyArticle',
    props: ['tittle','author']
}
</script>

// App 父组件
<template>
    <h3>App root</h3>
    <my-article :tittle="info.title" :author="info.author + '编著'"></my-article>
</template>

<script>
import MyArticle from './MyArticle.vue'

export default {
    name: 'MyApp',
    data() {
        return {
            info: {
                title: '标题1',
                author: '作者1'
            }
        }
    },
    components: {
        MyArticle
    }
}
</script>
```

#### 5.6 - props 的大小写命名

组件中如果使用“<span style="color: #e3371e">camelCase</span>( <span style="color: #e3371e">驼峰命名法</span> )”声明了 props 属性的名称，则有两种方式为其绑定属性的值(仅传递属性值时允许，定义，引用时需保持一致)

- 直接使用“驼峰命名”形式

    ```vue
    <my-article pubTime="1989"></my-article>
    ```

- 也可使用“短横线分割命名”形式

    ```vue
    <my-article pub-time="1989"></my-article>
    ```

### 6 - props 验证

#### 6.1 - props 验证介绍

- 使用<span style="color: #e3371e">数组类型</span>的 props 节点的缺点：<span style="color: #0099dd">无法</span>为每个 props <span style="color: #0099dd">指定具体的数据类型</span>

- props验证指：在封装组件时<span style="color: #e3371e">对外界传递过来的 props 数据</span> 进行合法性的校验，从而防止数据不合法的问题

    ![](vue3.assets/09-props验证.png)

#### 6.2 - 对象类型的 props 节点

使用<span style="color: #e3371e">对象类型</span>的 props 节点，可以对每个 props 进行<span style="color: #0099dd">数据类型的校验</span>

![](vue3.assets/09-props对象类型.png)

#### 6.3 - props 验证

对象类型的 props 节点提供了多种数据验证方案

- 基础的类型检查

    - 支持的 8 种类型：String、Number、Boolean、Array、Object、Date、Function、Symbol

- 多个可能的类型

    - 通过“<span style="color: #0099dd">数组</span>”的形式，指定多个可能的类型

    - ```javascript
        props: {
        	// PropA 属性的值可以是 类型1 或 类型2
        	propA:[Type1, Type2]
        }
        ```

- 必填项校验

    - 通过“配置<span style="color: #0099dd">对象</span>”的形式，来定义 prop 属性的 “验证规则”
    - 类型通过 <span style="color: #e3371e">`type：value`</span> 指定，必填通过 <span style="color: #e3371e">`required：true`</span> 指定

- 属性默认值

    - 通过“配置<span style="color: #0099dd">对象</span>”的形式，来定义 prop 属性的 “验证规则”
    - 类型通过 <span style="color: #e3371e">`type：value`</span> 指定，通过 <span style="color: #e3371e">`default：value`</span> 添加默认值

- 自定义验证函数

    - 为 props 属性指定自定义验证函数，对<span style="color: #0099dd"> props 属性的值进行更加精确的控制</span>
    - <span style="color: #e3371e">`validator(value) {}`</span>

```javascript
app.component('my-component', {
  props: {
    // 基础的类型检查 (`null` 和 `undefined` 会通过任何类型验证)
    propA: Number,
    // 多个可能的类型
    propB: [String, Number],
    // 必填的字符串
    propC: {
      type: String,
      required: true
    },
    // 带有默认值的数字
    propD: {
      type: Number,
      default: 100
    },
    // 带有默认值的对象
    propE: {
      type: Object,
      // 对象或数组默认值必须从一个工厂函数获取
      default: function() {
        return { message: 'hello' }
      }
    },
    // 自定义验证函数
    propF: {
        // “属性的值”可以通过形参 value 进行接收
      validator: function(value) {
	// 这个值必须匹配下列字符串中的一个，返回值为 true 表示通过，false 表示失败
        return ['success', 'warning', 'danger'].indexOf(value) !== -1
      }
    },
    // 具有默认值的函数
    propG: {
      type: Function,
      // 与对象或数组默认值不同，这不是一个工厂函数 —— 这是一个用作默认值的函数
      default: function() {
        return 'Default function'
      }
    }
  }
})
```

### 7 - 自定义事件

#### 7.1 - 自定义事件介绍

- 在封装组件时，为了让<span style="color: #e3371e">组件的使用者</span>可以<span style="color: #e3371e">监听到组件内状态的改变</span>，此时需要用到<span style="color: #e3371e">组件的自定义事件</span>

    ![](vue3.assets/10-自定义事件.png)

#### 7.2 - 自定义事件的 3 个使用步骤

- 封装组件时

    - <span style="color: #e3371e">声明</span>自定义事件

        - 开发者为自定义组件封装的自定义事件，必须事先在 <span style="color: #e3371e">emits 节点</span>中声明

            ```html
                <!-- 子组件 template -->
            	<h3>Counter child</h3>
                <p>counter的值是：{{ counter }}</p>
                <button @click="add">+ 1</button>
            ```

            ```javascript
                // 子组件 script
            	name: 'MyCounter',
                // 1.声明自定义事件
                emits: ['countChange'],
            ```

    - <span style="color: #e3371e">触发</span>自定义事件

        - 在 emits 节点下声明的自定义事件，可通过 <span style="color: #e3371e">this.$emit('自定义事件名')</span> 方法触发

        - <span style="color: #0099dd">事件名</span>：不同于组件和 prop，事件名不存在任何自动化的大小写转换。而是触发的事件名需要<span style="color: #0099dd">完全匹配</span>监听这个事件所用的名称。推荐始终使用 **kebab-case 的事件名**

            ```javascript
            	// 子组件 script
            	methods: {
                    add() {
                        this.counter += 1;
                        // 2.找到对应函数，调用 this.$emit() 方法触发自定义事件
                        this.$emit('countChange');
                    },
                },
            ```

- 使用组件时

    - <span style="color: #e3371e">监听</span>自定义事件

        - 使用自定义组件时，可通过 <span style="color: #e3371e">v-on</span> 的形式<span style="color: #e3371e">监听自定义事件</span>

            ```html
            	<!-- 父组件 template -->
            	<h2>App Root</h2>
                <my-counter @countChange="getCounter"></my-counter>
            ```

            ```javascript
            	// 父组件 script
            	    methods: {
                        // 绑定的事件处理函数
                    getCounter() {
                        console.log('触发了 countChange 自定义事件');
                    },
                },
            ```

#### 7.3 - 自定义事件传参

在调用  <span style="color: #e3371e">this.$emit('自定义事件名')</span> 方法触发自定义事件时，可通过<span style="color: #e3371e">第 2 个参数</span>为自定义事件传参，并通过事件处理函数的形参接收变化了的数据

```javascript
    // 子组件
	methods: {
        add() {
            this.counter += 1;
            // 2.找到对应函数，调用 this.$emit() 方法触发自定义事件
            // 将变化了的数据传递出去
            this.$emit('countChange', this.counter);
        },
    },
```

```javascript
 	// 父组件
	methods: {
        // 通过事件处理函数的形参接收变化了的数据
        getCounter(val) {
            console.log('触发了 countChange 自定义事件', val);
        },
    },
```

### 8 - 组件上的 v-model 指令

v-model 是双向数据绑定指令，当<span style="color: #e3371e">需要维护组件内外数据的同步时</span>，可以在组件上使用 v-model 指令

#### 8.1 - 组件上使用 v-model 的作用

- <span style="color: #e3371e">外界数据的变化</span>会<span style="color: #e3371e">自动同步</span>到组件中
- 组件中数据的变化，也会<span style="color: #e3371e">自动同步到外界</span>

![](vue3.assets/11-组件上的v-model.png)

#### 8.2 - 组件上使用 v-model 的步骤

##### 8.2.1 - 父组件→子组件 同步数据

![](vue3.assets/11-组件上的v-model-父向子.png)

- 父组件通过 <span style="color: #e3371e">v-bind: </span>属性绑定的形式，把数据传递给子组件

    ```html
        <!-- 父组件 -->
    	<h2>App Root</h2>
        <p>count 的值是：{{ count }}</p>
        <button @click="count += 1">+ 1</button>
        <my-counter :number="count"></my-counter>
    ```

- 子组件中，通过 <span style="color: #e3371e">props</span> 接收父组件传递过来的数据

    ```html
        <!-- 子组件 -->
    	<h3>Counter child</h3>
        <p>count 的值是：{{ number }}</p>
    ```

    ```javascript
    // 子组件
    export default {
        name: 'MyCounter',
        props: ['number'],
    };
    ```

##### 8.2.1 - 子组件→父组件 同步数据

![](vue3.assets/11-组件上的v-model-子向父.png)

- 在 v-bind: 指令之前添加 <span style="color: #e3371e">v-model</span> 指令

    - 希望对传递的 number 进行双向数据绑定

        ```html
        	<!-- 父组件 -->
        	<h2>App Root</h2>
            <p>count 的值是：{{ count }}</p>
            <button @click="count += 1">+ 1</button>
            <my-counter v-model:number="count"></my-counter>
        ```

- 在子组件中声明 <span style="color: #e3371e">emits</span> 自定义事件，格式为 <span style="color: #e3371e">update:</span>xxx，xxx为需要更新的属性值

    ```javascript
    	// 子组件
    	name: 'MyCounter',
        props: ['number'],
        emits: ['update:number'],
    ```

- 调用 <span style="color: #e3371e">$emit()</span> 触发自定义事件，更新父组件的数据

    ```html
        <!-- 子组件 -->
    	<h3>Counter child</h3>
        <p>count 的值是：{{ number }}</p>
        <button @click="add">+ 1</button>
    ```

    ```javascript
    	// 子组件
    	    name: 'MyCounter',
        props: ['number'],
        emits: ['update:number'],
        methods: {
            add() {
                this.$emit('update:number', this.number + 1);
            },
        },
    ```

## 五、组件高级

### 1 - 组件的生命周期

#### 1.1 - 组件的运行过程

![](vue3.assets/12-组件运行过程.png)

<span style="color: #e3371e">组件的生命周期</span>指的是：组件从<span style="color: #0099dd">创建</span> -> <span style="color: #0099dd">运行</span>（渲染） -> <span style="color: #0099dd">销毁</span>的整个过程，强调的是一个<span style="color: #49bf51">时间段</span>

#### 1.2 - 如何监听组件的不同时刻

<span style="color: #e3371e">vue 框架</span>为组件<span style="color: #0099dd">内置了不同时刻的生命周期函数</span>，生命周期函数<span style="color: #49bf51">会伴随</span>着组件的运行而<span style="color: #49bf51">自动调用</span>

- 当<span style="color: #e3371e">组件在内存中被创建完毕</span>后，会自动调用 <span style="color: #e3371e">created</span> 函数
- 当组件被成功的<span style="color: #e3371e">渲染到页面上</span>之后，会自动调用 <span style="color: #e3371e">mounted</span> 函数
- 当组件被<span style="color: #e3371e">销毁完毕</span>之后，会自动调用 <span style="color: #e3371e">unmounted</span> 函数

#### 1.3 - 如何监听组件的更新

当组件的 <span style="color: #0099dd">data 数据更新</span>之后，vue 会<span style="color: #49bf51">自动重新渲染组件</span>的 DOM 结构，从而保证<span style="color: #49bf51"> view 视图</span>展示的数据和 <span style="color: #49bf51">model 数据源</span>保持一致

- 当组件被<span style="color: #e3371e">重新渲染完毕</span>之后，会自动调用 <span style="color: #e3371e">updated</span> 函数

#### 1.4 - 组件中主要的生命周期函数

|                 生命周期函数                  |           执行时机           |                   所属阶段                   | 执行次数  |       应用场景       |
| :-------------------------------------------: | :--------------------------: | :------------------------------------------: | :-------: | :------------------: |
|  <span style="color: #49bf51">created</span>  |    组件在内存中创建完毕后    | <span style="color: #49bf51">创建</span>阶段 | 唯一 1 次 | 发 ajax 请求初始数据 |
|  <span style="color: #49bf51">mounted</span>  |  组件初次在页面中渲染完毕后  | <span style="color: #49bf51">创建</span>阶段 | 唯一 1 次 |    操作 DOM 元素     |
|  <span style="color: #0099dd">updated</span>  | 组件在页面中被重新渲染完毕后 | <span style="color: #0099dd">运行</span>阶段 | 0 或 多次 |                      |
| <span style="color: #ff8b24">unmounted</span> |  组件被销毁后（页面和内存）  | <span style="color: #ff8b24">销毁</span>阶段 | 唯一 1 次 |                      |

注意：在实际开发中，<span style="color: #e3371e"> created </span>是<span style="color: #e3371e">最常用</span>的生命周期函数

#### 1.5 - 组件中主要的生命周期函数

|                   生命周期函数                    |           执行时机           |                   所属阶段                   | 执行次数  |       应用场景       |
| :-----------------------------------------------: | :--------------------------: | :------------------------------------------: | :-------: | :------------------: |
| <span style="color: #ab04d9">before</span>Create  |     在内存中创建组件之前     | <span style="color: #49bf51">创建</span>阶段 | 唯一 1 次 |                      |
|    <span style="color: #49bf51">created</span>    |    组件在内存中创建完毕后    | <span style="color: #49bf51">创建</span>阶段 | 唯一 1 次 | 发 ajax 请求初始数据 |
|  <span style="color: #ab04d9">before</span>Mount  |   在粗剪初次渲染到页面之前   | <span style="color: #49bf51">创建</span>阶段 | 唯一 1 次 |                      |
|    <span style="color: #49bf51">mounted</span>    |  组件初次在页面中渲染完毕后  | <span style="color: #49bf51">创建</span>阶段 | 唯一 1 次 |    操作 DOM 元素     |
| <span style="color: #ab04d9">before</span>Update  |     在组件被重新渲染之前     | <span style="color: #0099dd">运行</span>阶段 | 0 或 多次 |                      |
|    <span style="color: #0099dd">updated</span>    | 组件在页面中被重新渲染完毕后 | <span style="color: #0099dd">运行</span>阶段 | 0 或 多次 |                      |
| <span style="color: #ab04d9">before</span>Unmount |       在组件被销毁之前       | <span style="color: #ff8b24">销毁</span>阶段 | 唯一 1 次 |                      |
|   <span style="color: #ff8b24">unmounted</span>   |  组件被销毁后（页面和内存）  | <span style="color: #ff8b24">销毁</span>阶段 | 唯一 1 次 |                      |

##### 不在 beforeCreate 中发 ajax 请求初始数据的原因

在拿到 ajax 返回的数据后，需要将数据存储到 data 中，以便组件渲染时能访问 data 里的数据。

beforeCreate 中，无法访问 data 里的数据，因此最早只能在 created 中发 ajax 请求初始数据

##### 不在 beforeMount 中操作 DOM 的原因

在 mouted 执行时，才第一次将当前组件渲染到页面中，beforeMount 执行时，还未完成渲染

#### 1.6 - 完整的生命周期图示

![](vue3.assets/lifecycle-1653118709804.png)

### 2 - 组件之间的数据共享

#### 2.1 - 组件之间的关系

项目开发中，组件之间的关系分为 3 种

- 父子关系

- 兄弟关系

- 后代关系

    ![](vue3.assets/13-组件之间的关系.png)

#### 2.2 - 父子组件之间的数据共享

父子组件之间的数据共享非为：

- <span style="color: #e3371e">父 ->子</span> 共享数据
- <span style="color: #e3371e">父 <-子</span> 共享数据
- <span style="color: #e3371e">父 <->子</span> 共享数据

##### 2.2.1 - 父组件向子组件共享数据

![](vue3.assets/11-组件上的v-model-父向子-1653120093826.png)

- 父组件通过 <span style="color: #e3371e">v-bind: </span>属性绑定的形式，把数据传递给子组件

    ```html
        <!-- 父组件 -->
    	<h2>App Root</h2>
        <p>count 的值是：{{ count }}</p>
        <button @click="count += 1">+ 1</button>
        <my-counter :number="count"></my-counter>
    ```

- 子组件中，通过 <span style="color: #e3371e">props</span> 接收父组件传递过来的数据

    ```html
        <!-- 子组件 -->
    	<h3>Counter child</h3>
        <p>count 的值是：{{ number }}</p>
    ```

    ```javascript
    // 子组件
    export default {
        name: 'MyCounter',
        props: ['number'],
    };
    ```

##### 2.2.2 - 子组件向父组件共享数据

- 在子组件中，通过 emits 节点声明自定义事件

    ```html
        <h3>Son Child</h3>
        <p>{{ num }}</p>
        <button @click="add">+ 1</button>
    ```

- 数据变化时，通过 $.emit() 触发自定义事件，并将变化后的数据传递出去

    ```javascript
        name: 'MySon',
        props: ['num'],
        emits: ['numChange'],
        methods: {
            add() {
                this.$emit('numChange', this.num + 1)
            },
        },
    ```

- 父组件通过 v-on 指令监听子组件的自定义事件，在父组件指定的事件处理函数中，通过形参拿到传递的数据

    ```html
        <h2>App Root —— {{ count }}</h2>
        <button @click="count += 1">+ 1</button>
    	<my-son :num="count" @numChange="getNum"></my-son>
    ```

    ```javascript
        data() {
            return {
                count: 0,
            }
        },
        methods: {
            getNum(num) {
                this.count = num
            },
        },
    ```

##### 2.2.3 - 父子组件之间数据的双向同步

使用 v-model

好处：

- 父组件中不用在监听自定义事件，也不用声明事件处理函数

![](vue3.assets/11-组件上的v-model-子向父-1653120236962.png)

- 在 v-bind: 指令之前添加 <span style="color: #e3371e">v-model</span> 指令

    - 希望对传递的 number 进行双向数据绑定

        ```html
        	<!-- 父组件 -->
        	<h2>App Root</h2>
            <p>count 的值是：{{ count }}</p>
            <button @click="count += 1">+ 1</button>
            <my-counter v-model:number="count"></my-counter>
        ```

- 在子组件中声明 <span style="color: #e3371e">emits</span> 自定义事件，格式为 <span style="color: #e3371e">update:</span>xxx，xxx为需要更新的属性值

    ```javascript
    	// 子组件
    	name: 'MyCounter',
        props: ['number'],
        emits: ['update:number'],
    ```

- 调用 <span style="color: #e3371e">$emit()</span> 触发自定义事件，更新父组件的数据

    ```html
        <!-- 子组件 -->
    	<h3>Counter child</h3>
        <p>count 的值是：{{ number }}</p>
        <button @click="add">+ 1</button>
    ```

    ```javascript
    	// 子组件
    	    name: 'MyCounter',
        props: ['number'],
        emits: ['update:number'],
        methods: {
            add() {
                this.$emit('update:number', this.number + 1);
            },
        },
    ```

##### 2.2.4 - 兄弟组件之间的数据共享

<span style="color: #e3371e">兄弟组件之间</span>实现数据共享的方案是 EventBus 。

可以借助第三方的包 <span style="color: #e3371e">mitt</span> 来创建 <span style="color: #e3371e">eventBus 对象</span>，从而实现兄弟组件之间的数据共享

![](vue3.assets/14-eventBus.png)

- 安装 mitt 包，导入 mitt 包，调用 mitt( )，返回值为 EventBus 对象，用 bus 常量接收，向外导出 bus对象
- 数据接收方
    - 导入并得到 EventBus 实例对象
    - 调用 EventBus 的 on( ) 方法，声明自定义事件，并通过事件回调接收数据
- 数据发送方
    - 导入并得到 EventBus 实例对象
    - 调用 EventBus 的 emit( ) 方法，向外发送数据

## 六、Class 与 Style 绑定

实际开发中常遇到<span style="color: #e3371e">动态操作元素 class 和 内联style </span>

因为它们都是 attribute，vue 允许开发者通过 <span style="color: #e3371e"> v-bind </span>属性绑定指令，为元素动态绑定<span style="color: #e3371e"> class 属性的值</span>和<span style="color: #e3371e">行内的 style 样式</span>

### 1 - 动态绑定 HTML 的 class

#### 1.1 - 三元表达式

通过<span style="color: #e3371e">三元表达式，动态地为元素绑定 class 的类名</span>

```vue
<template>
	// 利用三元表达式，动态绑定 class
    <h3 class="thin" :class="isItalic ? 'italic' : ''">Style</h3>
	// 为按钮绑定点击事件，切换 isItalic 的布尔值
    <button @click="isItalic=!isItalic">Toggle Italic</button>
    <p>Lorem ipsum dolor sit.</p>
</template>

<script>
export default {
    name: 'MyStyle',
    data() {
        return {
            isItalic: false
        }
    }
}
</script>

<style lang="less" scoped>
.thin {
    font-weight: 200;
}

.italic {
    font-style: italic;
}
</style>
```

#### 1.2 - 以 数组语法 绑定 HTML 的 Class

如果元素需要<span style="color: #e3371e">动态绑定多个 Class </span>类名，此时可使用<span style="color: #e3371e">数组的语法格式</span>

```vue
<template>
    <h3 class="thin" :class="[isItalic ? 'italic' : '',isDelete ? 'delete' : '']">Style</h3>
    <button @click="isItalic=!isItalic">Toggle Italic</button>
    <button @click="isDelete=!isDelete">Toggle Delete</button>
    <p>Lorem ipsum dolor sit.</p>
</template>

<script>
export default {
    name: 'MyStyle',
    data() {
        return {
            isItalic: false,
            isDelete: false
        }
    }
}
</script>

<style lang="less" scoped>
.thin {
    font-weight: 200;
}

.italic {
    font-style: italic;
}

.delete {
    text-decoration: line-through;
}
</style>
```

不过，当有多个条件 class 时，这样写太繁琐。所以在<span style="color: #e3371e">数组语法中也可以使用对象语法</span>用以简化

#### 1.3- 以 对象语法 绑定 HTML 的 Class

```vue
  <h3
    class="thin"
    :class="classObj"
  >Style</h3>
  <button @click="classObj.italic=!classObj.italic">Toggle Italic</button>
  <button @click="classObj.delete=!classObj.delete">Toggle Delete</button>
  <p>Lorem ipsum dolor sit.</p>
  
  data() {
    return {
      classObj: {
        italic: false,
        delete: false,
      },
    };
  },
```

### 2 - 动态绑定 HTML 的内联 style

#### 2.1 - 以 对象语法 绑定 HTML 的内联 style

- `:style` 的对象语法十分直观——看着非常像 CSS，但其实是一个 JavaScript 对象。

- CSS property 名可以用驼峰式 (camelCase) 或短横线分隔 (kebab-case，记得用引号括起来) 来命名

    ```html
    <div :style="{ color: activeColor, fontSize: fontSize + 'px'， 'background-color': bgcolor}"></div>
    <button @click="fontSize += 1">字号 + 1</button>
    ```

    ```javascript
    data() {
      return {
        activeColor: 'red',
        fontSize: 30，
        bgcolor: 'pink'
      }
    }
    ```

- 直接绑定到一个样式对象通常更好，这会让模板更清晰

    ```html
    <div :style="styleObject"></div>
    ```

    ```javascript
    data() {
      return {
        styleObject: {
          color: 'red',
          fontSize: '13px'
        }
      }
    }
    ```

#### 2.2 - 以 数组语法 绑定 HTML 的内联 style

- `:style` 的数组语法可以将多个样式对象应用到同一个元素上

- ```html
    <div :style="[baseStyles, overridingStyles]"></div>
    ```

## 七、计算属性与侦听器

### 1 - 计算属性介绍

计算属性<span style="color: #e3371e">本质</span>上就是一个 <span style="color: #e3371e">function 函数</span>，它可以<span style="color: #0099dd">实时监听</span> data 中数据的变化，并 <span style="color: #e3371e">return 一个计算后的新值</span>，供组件渲染 DOM 时使用

- 对于任何包含响应式数据的复杂逻辑，你都应该使用**计算属性**

### 2 - 声明计算属性

- 计算属性需要以 <span style="color: #ab04d9">function 函数</span>的形式声明到组件的 <span style="color: #ab04d9">computed 选项</span>中

- 直接调用函数名即可

- 计算属性<span style="color: #e3371e">侧重</span>于得到一个<span style="color: #e3371e">计算的结果</span>，因此属性值<span style="color: #0099dd">必须有 return 返回值</span>

    ```html
    <input type="text" v-model="count" />
    <p>{{ count }} 乘以二的值：{{ plus }}</p>
    ```

    ```javascript
        data() {
            return {
                count: 2,
            };
        },
        computed: {
            plus() {
                return this.count * 2;
            },
        },
    ```

### 3 - 计算属性的使用注意点

- 计算属性<span style="color: #e3371e">必须</span><span style="color: #0099dd">定义在 computed 节点中</span>
- 计算属性<span style="color: #e3371e">必须</span><span style="color: #0099dd">是一个 function 函数</span>
- 计算属性<span style="color: #e3371e">必须</span><span style="color: #0099dd">有 return 值</span>
- 计算属性<span style="color: #e3371e">必须</span><span style="color: #0099dd">当做普通属性使用</span>

### 4 - 计算属性 vs 方法

- 计算属性
    - 会<span style="color: #e3371e">缓存计算的结果</span>，只有计算属性的<span style="color: #0099dd">依赖项发生变化</span>时，才会<span style="color: #0099dd">重新进行计算</span>
    - 因此计算属性的性能更好
- 方法
    - 不会缓存计算的结果，每当触发重新渲染时，调用方法将总会再次执行函数

### 5 - watch 侦听器介绍

<span style="color: #e3371e">watch 侦听器</span>允许开发者监视数据的变化，从而<span style="color: #e3371e">针对数据的变化作特定的操作</span>

### 6 - watch 侦听器的基本语法

开发者需要<span style="color: #e3371e">在 watch 节点下</span>，定义自己的侦听器

- 以需要监听的数据名作为函数名

- 函数传入的参数，第一个为<span style="color: #0099dd">变化后的新值</span>，第二个为<span style="color: #0099dd">变化前的旧值</span>

    ```html
        <h3>Watch child 侦听器的用法</h3>
        <input type="text" v-model.trim="username" />
    ```

    ```javascript
    	data() {
    		return {
                username: '',
            };
        },
    	watch: {
            // 监听 username 的值的变化
            // 形参列表中，第一个值时“变化后的新值”，第二个值是“变化前的旧值”
            username(newval, oldval) {
                console.log(newval);
                console.log(oldval);
            },
        },
    ```

### 7 - [异步加载中使用watch](https://www.javascriptc.com/vue3js/guide/computed.html#%E4%BE%A6%E5%90%AC%E5%99%A8)

### 8 - 使用命令式的 vm.$watch

- 参数：
    - `{string | Function} source`
    - `{Function | Object} callback`
    - `{Object} [options]`
        - `{boolean} deep`
        - `{boolean} immediate`
        - `{string} flush`

- 返回：`{Function} unwatch`

#### 8.1 - $watch

`$watch` 返回一个取消侦听函数，用来停止触发回调

```javascript
const app = Vue.createApp({
  data() {
    return {
      a: 1
    }
  }
})

const vm = app.mount('#app')

const unwatch = vm.$watch('a', cb)
// later, teardown the watcher
unwatch()
```

#### 8.2 - **deep**选项

当 watch 侦听的是一个<span style="color: #e3371e">对象</span>，如果<span style="color: #e3371e">对象中的属性值发生了变化</span>，则<span style="color: #e3371e">无法被监听到</span>

为了发现对象内部值的变化，可以在选项参数中指定 `deep: true`。注意监听数组的变更不需要这么做。

```javascript
vm.$watch('someObject', callback, {
  deep: true
})
vm.someObject.nestedValue = 123
// callback is fired
```

#### 8.3 - **immediate**选项

在选项参数中指定 `immediate: true` 将立即以表达式的当前值触发回调

```javascript
vm.$watch('a', callback, {
  immediate: true
})
// 立即以 `a` 的当前值触发 `callback`
```

注意，在带有 `immediate` 选项时，你不能在第一次回调时取消侦听给定的 property。

### 9 - 计算属性 vs 侦听器

- 计算属性
    - 侧重于监听<span style="color: #e3371e">多个值</span>的变化，最终计算并<span style="color: #0099dd">返回一个新值</span>
- 侦听器
    - 侧重监听<span style="color: #e3371e">单个数据</span>的变化，最终<span style="color: #0099dd">执行特定的业务处理，不需要有任何返回值</span>

## 风格指南

##### 1 - 组件名为多个单词

- 避免与现有及未来的 HTML 元素冲突（HTML 元素都是单个单词）

    ```javascript
    app.component('todo-item', {
      // ...
    })
    
    export default {
      name: 'TodoItem',
      // ...
    }
    ```

##### 2 - Pros 定义尽量详细，至少指定类型

```javascript
props: {
  status: String
}

// 更好的例子
props: {
  status: {
    type: String,
    required: true,

    validator: value => {
      return [
        'syncing',
        'synced',
        'version-conflict',
        'error'
      ].includes(value)
    }
  }
}
```

##### 3 - 为 v-for 设置 key 值

- 以便维护内部组件及其子树的状态，甚至在元素上维护可预测的行为

    ```html
    <ul>
      <li
        v-for="todo in todos"
        :key="todo.id"
      >
        {{ todo.text }}
      </li>
    </ul>
    ```

##### 4 - 避免 `v-if` 和 `v-for` 一起使用

- 永远不要把 v-if 和 v-for 同时用在同一个元素上。

##### 5 - 为组件样式设置作用域

##### 6 - 私有 property <!--名称-->