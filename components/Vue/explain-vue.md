# Vue Project

## 1. 创建方法:

### A. Vue Cli

​    <b>这里可以使用官方给出的 Cli 去进行项目的搭建工作, 使用此方法需要提前使用 npm 进行全局安装, 使用: `npm install --global vue-cli` 进行安装. 完成后使用下方命令进行配置 Vue 工程</b> 

```js
vue create app-name 
// 输入完成后可以使用官方配置的 Vue@3.x 或是 Vue@2.x 当然了, 也可以自己进行配置, 配置完成后还可以选择是否保存自己的设置
```

### B. Vite

​    <b>除了以上方法外, 还可以直接使用 Vite 官方提供的脚手架 API 创建项目, 且免安装! 比 Webpack 更快!</b> 

```js
// npm 使用
npm create vite@latest
// yarn 使用
yarn create vite // 加载完成后输入项目名后需要自行选择创建的脚手架类型, 这里可以直接选择 Vue
```

### C. Unpkg

​    <b>如果实在懒得下载也可以暂时使用 Unpkg 网站提供的链接进行 Vue 的基础使用. ( 不会构建 Vue 项目 <i style="color: red;">!important</i> )</b> 

```js
<script src="https://unpkg.com/vue@2"></script> // Vue@2.x
<script src="https://unpkg.com/vue@3"></script> // Vue@3.x
```

## 2. 插件安装

### A. VScode

​    <b>Vs Code ( 全称: Visual Studio Code ), 是一款很不错的编程软件, 其内部提供了更为便捷的插件模块, 及代码提示功能.</b> 

​    <b>下载地址: </b> [点击下载](https://code.visualstudio.com/) <b>&lt;= ctrl + click ( 点击 )</b>

#### 1. VsCode 内置命令

​    <b>为了方便后期更方便的使用 Vs Code 编辑器, 所以官方预留出了一些  API. 如: 制表位的 `$1, $2, $3`... 或 最终光标位置 `$0`</b> 

<b>Visual Studio Code 中的代码片段完整文档:</b> [点击进入](https://code.visualstudio.com/docs/editor/userdefinedsnippets#_snippet-syntax) 

##### A.  变量命令

``` vscode
// 当前选的 顶文本 或 空字符串
TM_SELECTED_TEXT

// 当前行的内容
TM_CURRENT_LINE

// 光标 或 空字符串下的单词内容
TM_CURRENT_WORD

// 基于零索引的行号
TM_LINE_INDEX

// 基于单索引的行号
TM_LINE_NUMBER

// 当前文档的文件名
TM_FILENAME

//当前文档的文件名, 无扩展名
TM_FILENAME_BASE

//当前文档的目录
TM_DIRECTORY

// 从盘符起 => 当前文件的绝对路径
TM_FILEPATH

// 从根目录起 => 当前文件的相对路径
RELATIVE_FILEPATH

// 剪贴板的内容
CLIPBOARD

// 打开的 工作空间 或 文件夹的名称
WORKSPACE_NAME

// 打开的工作空间或文件夹的路径
WORKSPACE_FOLDER

// 基于零索引的游标编号
CURSOR_INDEX

// 基于单索引的游标编号
CURSOR_NUMBER
```

##### B. 时间命令

```vscode
// 本年度
CURRENT_YEAR

// 当年的最后两位数
CURRENT_YEAR_SHORT

// 两位数的月份 (例如 "02")
CURRENT_MONTH

// 月份的全名 (例如 "July)
CURRENT_MONTH_NAME

//月份的简称 (例如 "Jul")
CURRENT_MONTH_NAME_SHORT

// 两位数的月份中的日期 (例如 "08")
CURRENT_DATE

// 星期(例如 "Monday")
CURRENT_DAY_NAME

// 星期简称(例如 "Mon")
CURRENT_DAY_NAME_SHORT

// 24 小时制格式的当前小时
CURRENT_HOUR

// 当前分钟以两位数表示
CURRENT_MINUTE

// 当前秒为两位数
CURRENT_SECOND

// 自 Unix 纪元以来的秒数
CURRENT_SECONDS_UNIX
```

##### C. 随机值

```vscode
// 6 个随机以 10 为基数的数字
RANDOM

// 6 个随机以 16 为基数的数字
RANDOM_HEX

// 版本 4 UUID
UUID
```

##### D. 注释命令

```vscode
// 前注释, 如: "/*" 或 "<!--"
BLOCK_COMMENT_START

// 后注释, 如: "*/" 和 "-->"
BLOCK_COMMENT_END

// 单注释
LINE_COMMENT
```

#### 2. Vue 代码段

```json
{
    "vue2Template": {
		"prefix": "vue2Template",
		"body": [
			"<template>",
			"    <div class=\"\">${TM_FILENAME_BASE}</div>",
			"</template>\n",
			"<script>",
			"export default {",
			"    name: '${TM_FILENAME_BASE}',",
			"    data() {",
			"        return {$1}",
			"    },",
            "    methods: {},",
            "    computed: {},",
            "    watch: {},",
            "    created() {},",
			"}",
			"</script>\n",
			"<style scoped>$2</style>"
		],
		"description": "Create a new Vue @2.x base template"
	},
    "vue2Props": {
        "prefix": "vue2Props",
        "body": [
			"<template>",
			"    <div class=\"\">${TM_FILENAME_BASE}</div>",
			"</template>\n",
			"<script>",
            "import {$1} from '$2'",
			"export default {",
			"    name: '${TM_FILENAME_BASE}',",
			"    props: {},",
			"    data() {",
			"        return {$3}",
			"    },",
            "    methods: {},",
            "    computed: {},",
            "    watch: {},",
            "    created() {},",
			"}",
			"</script>\n",
			"<style scoped>$4</style>"
		],
        "description": "Create a new Vue @2.x props template"
    },
    "vue2Less": {
        "prefix": "vue2Less",
        "body": [
            "<template>",
            "    <div class=\"\">$1</div>",
			"</template>\n",
			"<script>",
			"export default {",
			"    name: '${TM_FILENAME_BASE}',",
			"    data() {",
			"        return {$2}",
			"    },",
            "    methods: {},",
            "    computed: {},",
            "    watch: {},",
            "    created() {},",
			"}",
			"</script>\n",
			"<style lang=\"less\" scoped>$3</style>"
        ],
        "description": "Create a new Vue @2.x less template"
    },
    "vue2Scss": {
        "prefix": "vue2Sass",
        "body": [
            "<template>",
            "    <div class=\"\">$1</div>",
			"</template>\n",
			"<script>",
			"export default {",
			"    name: '${TM_FILENAME_BASE}',",
			"    data() {",
			"        return {$2}",
			"    },",
            "    methods: {},",
            "    computed: {},",
            "    watch: {},",
            "    created() {},",
			"}",
			"</script>\n",
			"<style lang=\"scss\" scoped>$3</style>"
        ],
        "description": "Create a new Vue @2.x scss template"
    },
    "vue2Ts": {
        "prefix": "vue2Ts",
        "body": [
            "<template>",
			"    <div class=\"\">${TM_FILENAME_BASE}</div>",
			"</template>\n",
			"<script lang=\"ts\">",
			"export default {",
			"    name: '${TM_FILENAME_BASE}',",
			"    data() {",
			"        return {$1}",
			"    },",
            "    methods: {},",
            "    computed: {},",
            "    watch: {},",
            "    created() {},",
			"}",
			"</script>\n",
			"<style scoped>$2</style>"
        ]
    },
    "vue3Template": {
        "prefix": "Vue3Template",
        "body": [
            "<template>",
            "    <div class=\"\">${TM_FILENAME_BASE}</div>",
            "</template>\n",
            "<script setup>",
            "import {$1} from 'vue'",
            "</script>\n",
            "<style scoped>$2</style>"
        ],
        "description": "Create a new Vue @3.x base template"
    },
    "vue3Less": {
        "prefix": "Vue3Less",
        "body": [
            "<template>",
            "    <div class=\"\">$1</div>",
            "</template>\n",
            "<script setup>",
            "import {$2} from 'vue'",
            "</script>\n",
            "<style lang=\"less\" scoped>$3</style>"
        ],
        "description": "Create a new Vue @3.x scss template"
    },
    "vue3Scss": {
        "prefix": "Vue3Scss",
        "body": [
            "<template>",
            "    <div class=\"\">$1</div>",
            "</template>\n",
            "<script setup>",
            "import {$2} from 'vue'",
            "</script>\n",
            "<style lang=\"scss\" scoped>$3</style>"
        ],
        "description": "Create a new Vue @3.x scss template"
    },
    "vue3Ts": {
        "prefix": "Vue3Ts",
        "body": [
            "<template>",
            "    <div class=\"\">$1</div>",
            "</template>\n",
            "<script setup lang=\"ts\">",
            "import {$2} from 'vue'",
            "</script>\n",
            "<style scoped>$3</style>"
        ],
        "description": "Create a new Vue @3.x Types template"
    }
}
```

​    <b style="color: #E6A23C">将以上代码复制到 VsCode => 用户代码片段

### B. Auto Rename Tag

​    <b>Auto Rename Tag 是一款标签同步插件, 当你需要修改 HTML 标签时, 它会在你修改前标签的同时, 修改后方的闭合标签.</b> 

​    <b>拓展 ID: `formulahendry.auto-rename-tag`</b> 

### C. Vue Language Features (Volar)

   <b>Vue Language Features (Volar) 是一款 Vue 语言的插件, 会对语句的判断方式进行修改, 譬如: `<a :href="baseLink"` 时正常的 HTML 代码检查并不认识带有冒号的 `href` 属性, 就会直接抛出一个书写错误的提示, 当安装完成后就不会再出现以上的误判情况了.</b> 

<b>拓展 ID: `Vue.volar`</b> 

<b style="color: red;">!import: 这里需要注意此插件不能与 Vue@2 的 `Vetur` 一同使用.</b>

### D. Prettier - Code formatter

​    <b>Prettier - Code formatter 插件是用来对代码进行最优风格的格式化插件, 它对基础的 HTML, JavaScript, Css 等都是生效的, 当然你也可以使其对 Vue, React, Sass, Less等语言都可以进行格式化处理.</b> 

<b>拓展 ID: `esbenp.prettier-vscode`</b> 

<b>配置项: `format on save` ( 当文件被保存时自动格式化代买 )</b> 

### E. ESLint

​    <b>ESLint  是一款 JavaScript 代码的检测工具, 可以检查 拼写错误 和 语法错误.</b> 

​    <b>拓展 ID: `dbaeumer.vscode-eslint`</b> 

### F.  Live Server

​    <b>Live Server 是一款非常好用的 HTML 服务器, 可以在 HTML 页面下使用快捷键组合: `Alt + L` 然后再点击 `Alt + O` 就可以在浏览器中启动实时预览的 HTML 页面.</b> 

​    <b>拓展 ID: `ritwickdey.LiveServer`</b> 

### G. TypeScript Vue Plugin (Volar)

​    <b>此插件是 Vue Language Features (Volar) 的 Types 版本, 可以兼容 TypeScript 语法, 以至于不会让默认的语法检查工具因语法不同而报错.</b> 

<b>拓展 ID: `Vue.vscode-typescript-vue-plugin`</b> 

### H. Colorful Comments

​    <b>Colorful Comments 是一个注释提示颜色插件, 通过注释前不同的符号改变颜色从而使注释一目了然更加醒目!</b> 

​    <b>拓展 ID: `ParthR2031.colorful-comments `</b> 

### I. CodeSnap (Optional)

​    <b>此项为可选项 ( Optional ), CodeSnap 是一款代码截图插件, 通过选中指定代码 =&gt;右击鼠标 =&gt; CodeSnpa 进行截图.</b>

​    <b>拓展 ID: `adpyke.codesnap `</b> 

  ### J. Code Translate ( Optional )

​    <b>Code Translate 是一个可以将选中单词翻译成中文的插件, 将鼠标移至单个单词上方时, 会显示单词的含义. 对于单词量较少的, 可以使用该插件进行辅助.</b> 

​    <b>拓展 ID: `w88975.code-translate`</b> 

 ## 3. Vue 基础

### 前言

​    <b>在学习之前需要准备一个基础的目录结构以及项目代码</b> 

<img src="./img/initVueInHTML.png" alt="初始化项目, 及项目结构" />

​    <b>完成以上操作后, 配置初始化的 Css 样式文件, 清除默认项:</b> 

```css
/* 配置一些基础样式 */

/* todo: 优先清除默认样式 */
* {
    margin: 0;
    padding: 0;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
}

/* ul, ol */
ul, ol {
    list-style: none;
}

/* button, input */
button, input {
    outline: none;
    border: none;
    background: none;
}

/* a */
a {
    text-decoration: none;
}

/* 设置默认 rem = 10px */
html {
    font-size: 62.5%;
}
```

​    <b>清除完成后, 接下来设置 Script 脚本, 找到 `./src/js/index.js` 文件, 打开它并开始进行配置: </b> 

```js
// 新建一个 Vue 实例
const app = Vue.createApp();

// 将 #app 元素作为挂载到 Vue 实例上
// 这里的 app 是一个 Vue 实例, 而 #app 是一个 DOM 中 id 为 app 的元素
app.mount('#app');
```

### A. data 属性

​    <b>data 属性是一个函数, 用来存储内容的属性, 其内部可以用来存放 Java Script 的所有类型内容, 且可以访问直属属性, 如指数属性下还有其余属性也可以通过对象的访问方式进行访问. ( 例如: obj.name )</b> 

```js
// 新建一个 Vue 实例
const app = Vue.createApp({
    // 设置数据
    data() {
        return {
            // 用于存放用户输入的内容, 存储的内容可以是 JavaScript 中的任何类型
            str: "字符串",
            num: 123,
            bool: true,
            isUndefined: undefined,
            isNull: null,
            arr: [1, 2, 3],
            obj: {
                id: 1,
                name: "对象"
            },
            isFunction: function () {
                console.log("函数");
            },
        }
    }
});

// 将 #app 元素作为挂载到 Vue 实例上
// 这里的 app 是一个 Vue 实例, 而 #app 是一个 DOM 中 id 为 app 的元素
app.mount('#app');
```

​    <b>在 data 中定义的属性可以直接在 Vue 实例的 DOM 中进行使用 ( 这里的 Vue 实例是刚刚创建的 `#app` DOM 元素 )</b> 

​    <b>在实例中使用 `{{ name }}` 的方式对 data 中的数据进行访问</b> 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vue 基础项目</title>
    <!-- 导入自己的样式文件 -->
    <link rel="stylesheet" href="./src/css/index.css">
</head>
<body>
    <div id="app">
        <div class="str-box">{{ str }}</div>
        <div class="num-box">{{ num }}</div>
        <div class="bool-box">{{ bool }}</div>
        <div class="arr-box">{{ arr }}</div>
        <div class="obj-box">{{ obj }}</div>
        <div class="null-box">{{ isNull }}</div>
        <div class="undefined-box">{{ isUndefined }}</div>
        <div class="fun-box">{{ isFunction }}</div>
    </div>

    <!-- 导入 Unpkg Vue@3 -->
    <script src="src/utils/vue.global.js"></script>
 
    <!-- 导入自己的 Vue 程序代码 -->
    <script src="./src/js/index.js"></script>
</body>
</html>
```

​    <b>经过以上书写后可以看到 HTML 中, data 的直属属性都被解析出来了:</b> 

<img src="./img/dataDemonstration.png" alt="BrowseDemonstration" />

​    <b>看到这里突然发现: null 和 undefined 没有任何内容, 是显示失败了吗? 其实并不然...只是因为一个表示 <i style="color: red;">空</i>, 另一个表示 <i style="color: red;">未定义</i> 所以是显示不出任何内容的. 而且在 Vue 处理时, 它默认就是将这两个值视为空白, 不显示! 但它也是有好处的, 譬如: 页面刚加载设置上面两个值, 用于占位也是一个不错的选择.</b> 

​    <b>除了直属的属性, 还有附属的 <i style="color: red;">子属性</i> 或是 <i style="color: red">数组元素</i> 也可以进行单独访问:</b>

```html
<!-- Array -->
<div>{{ arr[0] }}</div>

<!-- Object -->
<div>{{ obj.name }}</div>
```

​    <b>展示效果如下: ( 此处使用的是对象的使用方法 )</b> 

<img src="./img/browserDemonstration.png" alt="data 函数的对象属性如何取值" />

### B. v-bind 指令

​    <b>V-bind 属性用于属性的绑定, 因为在模板中不能直接使用 <i style="color: orange; text-decoration: underline;">\<a href="{{ xxx }}"\>\</a\></i> 的形式去进行属性的设置, 只能通过 `v-bind` 指令对属性值进行双向的绑定.正确的方式则是: <i style="color: #67C23A; text-decoration: underline;">\<a v-bind:href="{{ xxx }}"\>\</a\></i> 或 <i style="color: #67C23A; text-decoration: underline;">\<a :href="{{ xxx }}"\>\</a\></i> 来进行数据绑定.</b> 

​    <b style="font-style: italic;">※ 指令:  <u>是指 Vue 提供的一组可以在 HTML 模板中或是在 Vue 文件中可以直接使用的特殊属性. 如: v-bind、v-for、v-if 等. 用于实现数据绑定、循环数据、条件判断等...</u></b> 

```vue
<template>
    <!-- 此处为 HTML 模板, 为了便利所以直接使用的 Vue 模块, 但是用方法不变! -->
    <div id="app">
        <a :href="link">百度首页</a>
        <a v-bind:href="link">百度首页</a>
    </div>
</template>

<script>
// 此处只展示 Data 属性， 为了便利所以直接使用的 Vue 模块.
export default {
    name: 'App',
    data() {
        return {
            link: 'https://www.baidu.com',
        }
    }
}
</script>

```

### C. v-for 指令

​    <b>`v-for` 指令是将 data() 属性中的数据使用指定的 HTML 模板的方式将需要展示数据展开并遍历数据后放入到 HTML 模板中对应的位置并最终展示出来</b> 

<img src="./img/showLists.png" />

​     <b>一般来说要想将以上数据展示到 HTML 中需要使用以下 2 中最基础的方式:</b>

<b>1. 从 HTML 中直接书写:</b> 

```html
<div id="app">
    <h1>展示数据</h1>
    <div class="show-data">
        <div>数据 - 01</div>
        <div>数据 - 02</div>
        <div>数据 - 03</div>
        <div>数据 - 04</div>
        <div>数据 - 05</div>
    </div>
</div>
```

<b>2. 使用 js 面向 过程 或 对象 对 数组 或 对象 进行解析并导入到 HTML 对应的 DOM 元素中</b>

```html
<div id="app">
    <h1>展示数据</h1>
    <div class="show-data"></div>
</div>

<script>
    // A. 面向过程的方式
    // 1. 获取元素
    const showDataProcess = document.querySelector('.show-data')

    // 2. 设置一个数组，用于存储数据
    const dataProcess = [
        '数据 - 01 ( JS 过程 )',
        '数据 - 02 ( JS 过程 )',
        '数据 - 03 ( JS 过程 )',
        '数据 - 04 ( JS 过程 )',
        '数据 - 05 ( JS 过程 )',
    ]

    // 3. 循环数组，将数组中的数据一一添加到 .show-data 中
    dataProcess.forEach(item => {
        // 3.1 创建一个 div 元素
        const div = document.createElement('div')
        // 3.2 设置 div 元素的内容
        div.innerHTML = item
        // 3.3 将 div 元素添加到 .show-data 中
        showDataProcess.appendChild(div)
    })

    // B. 面向对象的方式
    // 1. 获取元素
    const showDataObj = document.querySelector('.show-data')

    // 2. 设置一个数组，用于存储数据
    const dataObj = [
        '数据 - 01 ( JS 对象 )',
        '数据 - 02 ( JS 对象 )',
        '数据 - 03 ( JS 对象 )',
        '数据 - 04 ( JS 对象 )',
        '数据 - 05 ( JS 对象 )',
    ]

    // 3. 创建一个解析数组并展示数据到 HTML 中的方法
    // arr: 需要展示的数组, ele: 需要展示到哪一个元素中
    function arrToHTML (arr, ele) {
        // 3.0 开始循环
        arr.forEach(item => {
            // 3.1 创建一个 div 元素
            const div = document.createElement('div')
            // 3.2 设置 div 元素的内容
            div.innerHTML = item
            // 3.3 将 div 元素添加到 .show-data 中
            ele.appendChild(div)
        })
    }

    // 4. 调用方法, 将数据展示出来
    arrToHTML(dataObj, showDataObj)

</script>
```

<img src="./img/showDataInJs.png" />

​    <b>虽然经过上方的书写以及图片显示浏览器最终的展示效果, 但以上方式不论哪一个都会产生很多代码. 虽然面向对象会比面向过程好一些, 但也还是逃不出写很多方法和数据的命运...</b> 

​    <b>接下来看看 Vue 中是如何书写的, 以及使用 `v-for` 指令可以带来那些便利.</b> 

```vue
<templante>
    <div id="app">
        <h1>展示数据</h1>
        <div class="show-data">
            <div>数据 - 01 ( HTML )</div>
            <div>数据 - 02 ( HTML )</div>
            <div>数据 - 03 ( HTML )</div>
            <div>数据 - 04 ( HTML )</div>
            <div>数据 - 05 ( HTML )</div>
            <div v-for="item in items">{{ item }}</div>
        </div>
    </div>
</templante>

<script>
export default {
    name: 'App',
    data() {
        return {
            items: [
                "数据 - 01 ( Vue )",
                "数据 - 02 ( Vue )",
                "数据 - 03 ( Vue )",
                "数据 - 04 ( Vue )",
                "数据 - 05 ( Vue )"
            ]
        }
    }
}
</script>
```

<img src=./img/showDataInVue.png />

​    <b>通过以上观察, Vue 仅仅使用了一份 HTML 代码, 以及一份相同的数据, 它就完成了对数据的展示操作. 大大减少了代码量. Vue 同时也支持 对象 格式的数据展示, 和正常使用数据时一样.</b> 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vue 基础项目</title>
    <!-- 导入自己的样式文件 -->
    <link rel="stylesheet" href="./src/css/index.css">
</head>
<body>
    <div id="app">
        <h1>展示数据</h1>
        <div class="show-data">
            
            <div v-for="item in items" :key="item.id">{{ item.content }}</div>
        </div>
    </div>
    
    <script>
    	const info = {
            data() {
                return {
                    lists: [
                        {
                            id: 1,
                            content: "数据 - 01 ( Vue )"
                        },
                        {
                            id: 2,
                            content: "数据 - 02 ( Vue )"
                        },
                        {
                            id: 3,
                            content: "数据 - 03 ( Vue )"
                        },
                        {
                            id: 4,
                            content: "数据 - 04 ( Vue )"
                        },
                        {
                            id: 5,
                            content: "数据 - 05 ( Vue )"
                        },
                    ]
                }
            }
        }
    </script>
</body>
</html>
```

​    <b>以上就是 `v-for` 的全部用法了. 不难发现使用 Vue 和不使用的代码量, 使用 Vue 脚手架可以大幅减少程序员在开发过程中的书写量, 从而也可以更快的开发, 进而提升效率减少代码庸于.</b> 

### D. v-if 指令

​    <b>`v-if` 是用于控制 HTML 的组件是否呈现出来, 如果值为 "真 ( true )" 则加载, 否则则不加载. (真值: 1, true, 非空字符串; 假值: 0, false, undefined, null, "" )</b> 

```vue
<template>
    <div class="index-project">
        <h2 v-if="foodItems <= 0">{{ title.null }}</h2>
        <div v-else="isShow > 0">
            <h2>{{ title.has }}</h2>
            <ul>
                <li
                    class="food-item"
                    v-for="(item, index) in foodItems"
                    :key="index"
                > {{ index + 1 }}. {{ item }}</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Index',
    data() {
        return {
            title: {
                null: '暂时没有选取任何食物',
                has: '当前选取的食物有:'
            },
            foodItems: ["牛香咖啡", "奥良烤鸡", "油炸花生", "清蒸龙虾"]
        }
    }
};
</script>
```

​    <b>当有食物的时候则会显示到 HTML 的 DOM 元素中. 如下所示:</b> 

<img src="./img/vIfBrowser.png" />

​    <b>当没有食物时则会按照预先设置的那样, 走到 `v-if` 分支时就会加载第一项 ( `v-if="foodItems <= 0"` ) 也就是说当食物小于 0 或等于 0 时就会显示第一个 HTML 选项, 我们将 Vue 中的 `foodItems` 项清空再来查看浏览器最终的渲染结果. 如图所示: </b> 

<img src="./img/vIfNull.png" />

​    <b>最终的选然还是取决于是否有食物的数值, `v-if` 会根据最终条件判断是否渲染该部分结构.</b> 

<b>案例: 01</b>

​    <b>使用 `v-if` 配合点击事件使提问框中的答案按照需求决定是否显示.</b> 

```vue
<template>
    <div class="index-project">
        <div class="question-box">
            <h1>拓展提高</h1>
            <p>在日语中 "手紙 [ てがみ ]" 在日语中的含义.</p>
            <p v-if="isShow">"手紙 [ てがみ ]" 在日语中的含义是: 信 Or 信件 的意思.</p>
            <button @click="isShow = !isShow">{{ isShow ? "隐藏" : "显示" }}答案</button>
        </div>
    </div>
</template>

<script>

export default {
    name: 'index',
    data() {
        return {
            isShow: false,
        }
    },
}
</script>

<style lang="scss" scoped>
.index-project {
    display: flex;
    width: 100vw;
    height: 100vh;
    justify-content: center;
    align-items: center;
    font-size: 1.6rem;

    .question-box {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        width: 60rem;
        height: 20rem;
        box-shadow: 0 0 1rem rgba(0, 0, 0, 0.2);
        box-sizing: border-box;
        padding: 2rem;

        button {
            width: 10rem;
            height: 4rem;
            align-self: end;
            font-weight: 700;
            color: #fff;
            background-color: #409EFF;
            outline: none;
            border: none;
            border-radius: .5rem;
            margin-right: 3rem;
            cursor: pointer;

            &:hover {
                background-color: #a0cfff;
            }
        }
    }
}
</style>

```

<img src="./img/questionNone.png" />

<img src="./img/questionShow.png" />

​    <b>经过以上练习基本上就可以掌握 Vue 中 `v-if` 的基本用法了. 但需要注意的是 `v-if` 和 `v-else-if` 以及 `v-else` 与普通 JavaScript 中的判断语句使用方式一致, 所以也就是说以上所有的判断性 DOM 元素都必须相邻使用, 每一组 `v-if` 都不能在判断时被分隔. 还有一点需要注意的是: `v-if` 是决定该数据在 HTML 中是否被渲染, 也就是说如果是 false 的话就不会创建元素, 而还有一个与其很相似的指令 `v-show` 决定的是该元素是否在 DOM 中显示, 而不是是否渲染, 最终呈现的则是: `<dom style="display: none;">v-show 的效果</dom>` 最终该元素只是在样式中被隐藏了, 而不是没有被渲染.</b> 

### E. 创建事件

​    <b>经过以上的练习也可以大概知道如何创建事件了, 不过那是简写方式 `@事件名称` 而全拼则是: `v-on:事件名称`, 需要注意的是: 这里的所有事件名称都不需要加上 `on` 如: `onclic` 则是 `@click` 或是 `v-on:click` 的形式, 以此类推.</b>

### F. computed 计算属性

​    <b>计算属性: `computed` 则是为了避免在 HTML 模板中书写过多的逻辑属性, 如上方 ( D )练习中使用的`{{ isShow ? "隐藏" : "显示" }}答案`, 如果还有其他地方依旧用到了该属性, 那么就还需要在 HTML 中反复书写... 这非常不符合 Vue 逻辑且处理事件过多也会影响程序的运行速度, 并且程序员需要书写更多的代码大大降低了工作进程. 在这个时候就可以使用 Vue 提供的 `computed` 计算属性. </b> 

```vue
<template>
    <div class="index-project">
        <div class="question-box">
            <h1>拓展提高</h1>
            <p>在日语中 "手紙 [ てがみ ]" 在日语中的含义.</p>
            <p v-if="isShow">"手紙 [ てがみ ]" 在日语中的含义是: 信 Or 信件 的意思.</p>
            <button @click="isShow = !isShow">{{ isShowToStr }}答案</button>
        </div>
    </div>
</template>

<script>

export default {
    name: 'index',
    data() {
        return {
            isShow: false,
        }
    },
    computed: {
        isShowToStr () {
            return this.isShow ? "隐藏" : "显示"
        }
    }
}
</script>

<style lang="scss" scoped>
.index-project {
    display: flex;
    width: 100vw;
    height: 100vh;
    justify-content: center;
    align-items: center;
    font-size: 1.6rem;

    .question-box {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        width: 60rem;
        height: 20rem;
        box-shadow: 0 0 1rem rgba(0, 0, 0, 0.2);
        box-sizing: border-box;
        padding: 2rem;

        button {
            width: 10rem;
            height: 4rem;
            align-self: end;
            font-weight: 700;
            color: #fff;
            background-color: #409EFF;
            outline: none;
            border: none;
            border-radius: .5rem;
            margin-right: 3rem;
            cursor: pointer;

            &:hover {
                background-color: #a0cfff;
            }
        }
    }
}
</style>

```

### G. methods 函数属性

​    <b>Vue 除了提供计算属性也提供了 ( methods ) 函数属性, 多用于: 表单验证、Ajax 数据传递、事件函数等, 且在 Vue 中的 `methods` 内部定义函数的好处是可以直接使用 `this.` 的形式访问到 Vue 中 ` data()` 函数内所定义的数据. 且构思清晰减少 HTML 代码量, 并且还可以进行复用.</b>  

```vue
<template>
    <div class="index-project">
        <div class="question-box">
            <h1>拓展提高</h1>
            <p>在日语中 "手紙 [ てがみ ]" 在日语中的含义.</p>
            <p v-if="isShow">"手紙 [ てがみ ]" 在日语中的含义是: 信 Or 信件 的意思.</p>
            <button @click="isShowOpposite">{{ isShowToStr }}答案</button>
        </div>
    </div>
</template>

<script>

export default {
    name: 'index',
    data() {
        return {
            isShow: false,
        }
    },
    methods: {
        isShowOpposite () {
            return this.isShow = !this.isShow
        }
    },
    computed: {
        isShowToStr () {
            return this.isShow ? "隐藏" : "显示"
        }
    }
}
</script>

<style lang="scss" scoped>
.index-project {
    display: flex;
    width: 100vw;
    height: 100vh;
    justify-content: center;
    align-items: center;
    font-size: 1.6rem;

    .question-box {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        width: 60rem;
        height: 20rem;
        box-shadow: 0 0 1rem rgba(0, 0, 0, 0.2);
        box-sizing: border-box;
        padding: 2rem;

        button {
            width: 10rem;
            height: 4rem;
            align-self: end;
            font-weight: 700;
            color: #fff;
            background-color: #409EFF;
            outline: none;
            border: none;
            border-radius: .5rem;
            margin-right: 3rem;
            cursor: pointer;

            &:hover {
                background-color: #a0cfff;
            }
        }
    }
}
</style>

```

### H. watch 监听属性

​    <b>`watch` 监听属性, 用来监听属性变化的, 使用 `watch` 时需要使 <u>监听器名字</u> 与 <u>被监听的属性名</u> 一致, 监听器需要接受两个属性: `newVal` ( 新属性值 ) 和 `oldVal` ( 旧属性值 ) 作为参数.</b> 

```vue
<template>
    <div class="index-project">
        <div class="box">
            <h1>简单问答</h1>
            <p class="question">在日语中 "手紙 [ てがみ ]" 在日语中的含义.</p>
            <p class="answer" v-show="isShow">答: 手紙 [ てがみ ] 的意思是 "信件".</p>
            <button @click="isShowEvent">
                {{ isShowCom }}
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Index',
    data() {
        return {
            // 数据: 用于存储数据, 该数据可以被访问并使用
            isShow: false, // 是否显示答案
            countDown: 5, // 倒计时: 5秒
            timer: null, // 定时器
        }
    },
    computed: {
        // 计算属性: 用于计算数据, 该属性可以直接被访问并使用
        isShowCom() {
            // 返回值: 按照 isShow 数据进行计算并将结果返回, 该数据可以被直接访问并使用
            // 且该数据被多次访问时, 只会计算一次, 之后会将计算结果进行缓存, 直到数据发生变化时才会重新计算
            return this.isShow
                ? '显示答案' + this.countDown + '秒' // 如果为 "真" 则显示 "显示答案"
                : '隐藏答案' // 如果为 "假" 则显示 "隐藏答案"
        }
    },
    methods: {
        // 方法属性: 用于存储方法, 该方法可以直接被访问并使用
        isShowEvent() {
            // 作用: 用于控制答案的显示和隐藏
            // 该属性不会被缓存, 每次访问都会重新计算
            this.isShow = !this.isShow // 将 isShow 数据取反
        }
    },
    watch: {
        // 监听属性: 用于监听数据的变化, 该属性不可以直接被访问, 主要作用用于比较耗时的操作或是异步操作等
        // 在监听过程中会将新值和旧值传入到回调函数中, 最后将新值返回到 data 数据中, 再由 data 数据更新视图
        isShow(newVal, oldVal) {
            // 这里需要注意的是: 监听值 和 需要监听的数据名称保持一致
            if (newVal) {
                this.countDown = 5; // 重置倒计时
                if(this.timer) { // 判断如果定时器已经存在, 则清除定时器, 防止定时器叠加
                    clearInterval(this.timer) // 清除定时器, 作用: 为了防止用户多次点击按钮, 导致定时器叠加
                    this.timer = null; // 使定时器为空, 作用: 为了防止用户多次点击按钮, 导致定时器叠加
                }

                this.timer = setInterval(() => { // 设置定时器
                    this.countDown -= 1; // 倒计时减 1
                    if (this.countDown === 0) { // 如果倒计时为0, 则隐藏答案, 并清除定时器
                        this.isShow = false; // 隐藏答案
                        clearInterval(this.timer); // 清除定时器
                        this.timer = null; // 使定时器为空
                    }
                }, 1000)
            }
        }
    }
}
</script>

<style lang="scss" scoped>
.index-project {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    background-color: #f2f2f2;

    .box {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-between;
        width: 50vw;
        height: 50vh;
        background-color: #fff;
        border-radius: 10px;
        padding: 2rem;

        p {
            font-size: 2.4rem;
        }

        button {
            align-self: end;
            width: 8.6rem;
            height: 4rem;
            background-image: linear-gradient(45deg,
                    hsl(218deg, 100%, 50%) 0%,
                    hsl(187deg, 100%, 40%) 100%);
            font-weight: 600;
            color: #fff;
            border-radius: .4rem;
            cursor: pointer;
        }
    }
}
</style>
```

### 附录:

#### 1. computed 计算属性 与 methods 函数属性 的区别

​    <b>为了更好的使用 Vue 脚手架, 本次将对 computed 和 methods 进行区分测试. 测试数据如下:</b>

```js
const dataList = [
    "Vue.js 从入门到精通",
    "Vue 3.x 入门指南",
    "Vue.js 2.x 实战",
    "React 全家桶",
    "React 入门指南",
    "你不知道的 JavaScript 实战技巧"
]
```

​    <b>任务: 将dataList 中的数据进行筛选并输出到 HTML 中进行展示.</b> 

##### illustration 例图

<img src="./img/MethodsAndComputed01.png" />

##### computed 测试

​    <b>本次测试目的为辨别 computed 属性和 methods 属性的区别, 为了更好的区分将测试分为两部分进行展示, 该部分将使用 computed 完成筛选 dataList 内容中包含 Vue 的项目并称现在 HTML 无序列表中. 实现方法如下:</b> 

```vue
<template>
    <div class="index-project">
        <ul>
            <li v-for="content in isVue">
                {{ content }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'index',
    data() {
        return {
            dataList: [
                "Vue.js 从入门到精通",
                "Vue 3.x 入门指南",
                "Vue.js 2.x 实战",
                "React 全家桶",
                "React 入门指南",
                "你不知道的 JavaScript 实战技巧"
            ]
        }
    },
    computed: {
        isVue() {
            return this.dataList.filter(item => item.includes('Vue'))
        }
    },
}
</script>

<style lang="scss" scoped>
.index-project {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    min-height: 100vh;
    background-color: #333;
    padding: 20px;

    ul {
        color: white;
        font-size: 40px;

        li {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 20px;
        }
    }
}
</style>

```

##### methods 测试

​    <b>接下来使用 methods 完成筛选 dataList 内容中包含 Vue 的项目并称现在 HTML 无序列表中.</b> 

```vue
<template>
    <div class="index-project">
        <ul>
            <li v-for="content in getVue()">
                {{ content }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'index',
    data() {
        return {
            dataList: [
                "Vue.js 从入门到精通",
                "Vue 3.x 入门指南",
                "Vue.js 2.x 实战",
                "React 全家桶",
                "React 入门指南",
                "你不知道的 JavaScript 实战技巧"
            ]
        }
    },
    methods: {
        getVue() {
            return this.dataList.filter(item => item.includes('Vue'))
        }
    }
}
</script>

<style lang="scss" scoped>
.index-project {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    min-height: 100vh;
    background-color: #333;

    ul {
        color: white;
        font-size: 40px;

        li {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 20px;
        }
    }
}
</style>

```

<b style="color: #F56C6C;">※ 注意: 在使用 methods 函数属性时需要在后方加上小括号进行方法的调用</b> 

##### cache 缓存测试

<b>经过以上书写发现两者都可以对 dataList 中的内容进行筛选, 好像并没什么区别.为了更好的观测它们, 接下来对它们进行缓存测试, 给 HTML 中添加一个按钮, 并赋予其点击事件. 为了能够直观感受到是否真的运行了, 在 Vue 的 script 标签中, 或是 Js 文件中的 Vue 数据上给一个count 变量用来记录点击次数.代码如下:</b> 

```vue
<template>
    <div class="index-project">
        <ul>
            <li v-for="content in getVue()">
                {{ content }}
            </li>
        </ul>
        <button @click="count++">被点击了 {{ count }} 次</button>
    </div>
</template>

<script>
export default {
    name: 'index',
    data() {
        return {
            dataList: [
                "Vue.js 从入门到精通",
                "Vue 3.x 入门指南",
                "Vue.js 2.x 实战",
                "React 全家桶",
                "React 入门指南",
                "你不知道的 JavaScript 实战技巧"
            ],
            count: 0
        }
    },
    methods: {
        getVue() {
            console.log('getVue 被调用了')
            return this.dataList.filter(item => item.includes('Vue'))
        }
    },
    computed: {
        isVue() {
            console.log('isVue 被调用了')
            return this.dataList.filter(item => item.includes('Vue'))
        }
    }
}
</script>

<style lang="scss" scoped>
.index-project {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    min-height: 100vh;
    background-color: #333;

    ul {
        color: white;
        font-size: 40px;

        li {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 20px;
        }
    }

    button {
        width: 220px;
        height: 60px;
        padding: 10px 20px;
        color: white;
        font-size: 24px;
        background-color: #409EFF;
        border: none;
        outline: none;
        border-radius: 4px;
        cursor: pointer;
    }
}
</style>
```

​    <b>接下来分别使用以上两种方法进行测试, 得到的结果如下:</b> 

<b>methods 结果为:</b> 

<img src="./img/MethodsAndComputed02.png" />

<b>computed 结果为:</b>

<img src="./img/MethodsAndComputed03.png" />

##### summary 总结

<b style="color: #67C23A">经过以上测试得出:</b>

​    <b style="color: #67C23A;">1. computed 计算属性更适合做一些简单的操作.但 methods 函数属性则适合做一些业务性或逻辑性的复杂操作.</b> 

​    <b style="color: #67C23A;">2.computed 计算属性与 methods 函数属性相比, 计算属性会先比较数值是否发生变化, 如果没有变化则会优先读取缓存中的值.</b> 

​    <b style="color: #67C23A;">3. 计算属性可以直接用于 HTML 模板中, 与 data 数据属性的使用方法一致.</b> 

​    <b style="color: #67C23A;">5. methods 函数属性更适合作用于事件的监听或是公共业务的逻辑等...当然你也可以将其当作普通的 JavaScript 函数来使用或操作.</b> 

#### 2. computed 计算属性 与 watch 监听器 的区别

​    <b>为了更好的使用 Vue 脚手架, 本次将对 computed 和 watch 进行区分测试. 测试数据如下:</b> 

```js
const dataList = [];

dataList.push("JavaScript 悟道")
```

​    <b>任务:  通过一下方式对 dataList 内容条数进行统筹, 并通过后期点击 "添加图书" 对 dataList 数据新增 "JavaScript 悟道" 项, 并实时更新书本的数目以及 HTML 对图书的展示</b> 

##### illustration 例图

<b>base</b>

<img src="./img/WatchAndComputed01.png" />

<b>onClick</b> 

<img src="./img/WatchAndComputed02.png" />

##### computed 测试

​    <b>本次测试目的为辨别 computed 属性和 watch 属性的区别, 为了更好的区分将测试分为两部分进行展示, 该部分将使用 computed 完成对 dataList 内容计数, 并通过后期点击 "添加图书" 对 dataList 数据新增 "JavaScript 悟道" 项, 并实时更新书本的数目以及 HTML 对图书的展示. 实现方法如下:</b>

```vue
<template>
    <div class="index-project">
        <ul>
            <li v-for="content in dataList">
                {{ content }}
            </li>
        </ul>
        <div class="book-sum">
            当前图书共计 {{ bookSum }} 本
        </div>
        <button @click="addBook">
            添加图书
        </button>
    </div>
</template>

<script>
export default {
    name: 'index',
    data() {
        return {
            dataList: [
                "Vue.js 从入门到精通",
                "Vue 3.x 入门指南",
                "Vue.js 2.x 实战",
                "React 全家桶",
                "React 入门指南",
                "你不知道的 JavaScript 实战技巧"
            ],
        }
    },
    methods: {
        addBook() {
            // 判断 datdList 中是否存在 "JavaScript 悟道", 如果存在, 则不添加
            if (this.dataList.indexOf("JavaScript 悟道") === -1) {
                this.dataList.push("JavaScript 悟道")
            }
        }
    },
    computed: {
        bookSum() {
            return this.dataList.length
        }
    }
}
</script>

<style lang="scss" scoped>
.index-project {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    min-height: 100vh;
    background-color: #333;

    ul {
        color: white;
        font-size: 40px;

        li {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 20px;
        }
    }

    .book-sum {
        margin: 20px 0;
        color: white;
        font-size: 24px;
    }

    button {
        width: 220px;
        height: 60px;
        padding: 10px 20px;
        color: white;
        font-size: 24px;
        background-color: #409EFF;
        border: none;
        outline: none;
        border-radius: 4px;
        cursor: pointer;
    }
}
</style>

```

##### watch 测试

​    <b>接下来使用 watch 完成以上对新增项的计数功能</b> 

```vue
<template>
  <div class="index-project">
      <ul>
          <li v-for="content in dataList">
              {{ content }}
          </li>
      </ul>
      <div class="book-sum">
          当前图书共计 {{ sum }} 本
      </div>
      <button @click="addBook">
          添加图书
      </button>
  </div>
</template>

<script>
export default {
  name: 'index',
  data() {
      return {
          dataList: [
              "Vue.js 从入门到精通",
              "Vue 3.x 入门指南",
              "Vue.js 2.x 实战",
              "React 全家桶",
              "React 入门指南",
              "你不知道的 JavaScript 实战技巧"
          ],
          // 因为 watch 无法直接监听数组后产生的变换, 所以需要有一个变量来存储数组的长度
          // 再通过后期监听等方式进行改变
          sum: 0
      }
  },
  methods: {
      addBook() {
          // 判断 datdList 中是否存在 "JavaScript 悟道", 如果存在, 则不添加
          if (this.dataList.indexOf("JavaScript 悟道") === -1) {
              this.dataList.push("JavaScript 悟道")
          }
      }
  },
  computed: {
      bookSum() {
          return this.dataList.length
      }
  },
  watch: {
    // watch 在监听数组 或 对象 时发变化时, 需要使用 deep: true
      dataList: {
        deep: true, // deep 为 true 时, 监听数组中的每一项
        // handler 为默认的监听函数, 内部会传入 newVal (新值) 和 oldVal (旧值)
        handler(newVal) {
          // 通过改变 sum 的值, 来触发视图的更新
          this.sum = newVal.length
        }
      }
  },
  created() {
    // created 钩子中, 会在页面加载完毕后触发
    // 此外, 钩子有: ========================
    //     1. beforeCreate 作用: 在实例初始化之后, 数据观测(data observer) 和 event/watcher 事件配置之前被调用
    //     2. created 作用: 在实例创建完成后被立即调用, 在这一步, 实例已完成以下的配置: 数据观测(data observer), 属性和方法的运算, watch/event 事件回调
    //     3. beforeMount 作用: 在挂载开始之前被调用, 相关的 render 函数首次被调用
    //     4. mounted 作用: el 被新创建的 vm.$el 替换, 并挂载到实例上去之后调用该钩子
    //     5. beforeUpdate 作用: 数据更新时调用, 发生在虚拟 DOM 打补丁之前
    //     6. updated 作用: 由于数据更改导致的虚拟 DOM 重新渲染和打补丁, 在这之后会调用该钩子
    //     7. beforeDestroy 作用: 实例销毁之前调用, 在这一步, 实例仍然完全可用
    //     8. destroyed 作用: Vue 实例销毁后调用, 调用后, 所有的事件监听器会被移除, 所有的子实例也会被销毁
    // 因为 watch 无法在浏览器加载完自动触发, 所以需要在 created 钩子中手动修改 sum 的初始值
    // ====================================
    this.sum = this.dataList.length
  }
}
</script>

<style lang="scss" scoped>
.index-project {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 100vh;
  background-color: #333;

  ul {
      color: white;
      font-size: 40px;

      li {
          display: flex;
          justify-content: center;
          align-items: center;
          margin-bottom: 20px;
      }
  }

  .book-sum {
      margin: 20px 0;
      color: white;
      font-size: 24px;
  }

  button {
      width: 220px;
      height: 60px;
      padding: 10px 20px;
      color: white;
      font-size: 24px;
      background-color: #409EFF;
      border: none;
      outline: none;
      border-radius: 4px;
      cursor: pointer;
  }
}
</style>

```

##### summary 总结

​    <b>通过以上操作发现与之前的实验结果一样, 还是没有什么具体区别, 但实际上两者需要根据项目的实际情况进行区分使用.如:</b>

​    <b style="color: #67C23A;">1. computed 计算属性更适合简单的业务逻辑计算. 而 watch 监听属性则更偏向于一些耗时操作或是远程 API 的加载操作等...</b> 

​    <b style="color: #67C23A;">2. computed 可以直接出现在 HTML 或是 Vue 项目中的 template 模板中进行使用. 而 watch 则需要在 data 中新建变量 或 依靠原有的变量数据才能进行展示如上方计数需要依靠 sum 变量才能成功在 HTML 中展示 dataList 的长度.</b> 

​    <b style="color: #67C23A;">3. computed 是响应 data 数据变化, watch 则是响应数据变化</b> 

​    <b style="color: #67C23A;">4. computed 有返回值, 而 watch 没有返回值</b> 

​    <b style="color: #67C23A;">5. computed 属性可以设置 getter 和 setters 用于接收或修改 data 中的数据, 而 watch 则是仅可以修改 data 中的数据, 并没有 getter 和 setters 属性</b> 

##### demonstrate 演示

​    <b>演示 computed 计算属性的 getter 和 setters 的使用过程</b> 

```vue
<template>
  <div class="index-project">
      <ul>
          <li v-for="content in dataList">
              {{ content }}
          </li>
      </ul>
      <div class="book-sum">
          当前图书共计 {{ bookSum }} 本
      </div>
      <button @click="newBook = 'JavaScript 悟道'">
          添加图书
      </button>
  </div>
</template>

<script>
export default {
  name: 'index',
  data() {
      return {
          dataList: [
              "Vue.js 从入门到精通",
              "Vue 3.x 入门指南",
              "Vue.js 2.x 实战",
              "React 全家桶",
              "React 入门指南",
              "你不知道的 JavaScript 实战技巧"
          ],
          addNewBook: "", // 用于存储点击事件中的内容
          isLock: false, // 设置节流锁, 防止重复添加, 默认为 false
      }
  },
  computed: {
      bookSum() {
          return this.dataList.length
      },
      newBook: {
        // 通过 get 和 set 方法实现双向绑定
        get() {
          return this.addNewBook // 将 addNewBook 的值赋值给 newBook
        },
        set(val) {
          if (this.isLock === true) return; // 设置节流锁, 防止重复添加
          if (val === "") return; // 如果输入框为空, 则不添加
          if (this.addNewBook === val) return; // 如果输入框内容与添加的内容一致, 则不添加
          if (this.dataList.indexOf(val) !== -1) return; // 如果 datdList 中已存在该内容, 则不添加
          this.isLock = true // 设置节流锁, 防止重复添加, 上锁
          this.addNewBook = val // 将点击事件中的内容赋值给 addNewBook
          // 设置延时器, 2s 后将 addNewBook 添加到 dataList 中, 并解锁
          setTimeout(() => {
            this.dataList.push(val) // 将 addNewBook 添加到 dataList 中
            this.isLock = false // 解锁
          }, 2000) // 2s 后执行
        }
      }
  }
}
</script>

<style lang="scss" scoped>
.index-project {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 100vh;
  background-color: #333;

  ul {
      color: white;
      font-size: 40px;

      li {
          display: flex;
          justify-content: center;
          align-items: center;
          margin-bottom: 20px;
      }
  }

  .book-sum {
      margin: 20px 0;
      color: white;
      font-size: 24px;
  }

  button {
      width: 220px;
      height: 60px;
      padding: 10px 20px;
      color: white;
      font-size: 24px;
      background-color: #409EFF;
      border: none;
      outline: none;
      border-radius: 4px;
      cursor: pointer;
  }
}
</style>

```

#### 3. methods 函数属性 与 watch 监听器 的区别

   <b>比较了所有的 computed 计算属性, 只剩下 methods 函数属性 和 watch 监听属性没有比较了, 接下来看一下它们之间具体的区别是什么. </b> 

##### illustration 例图

​    <b>base</b>

<img src="./img/MethodsAndWatch01.png" />

​    <b>onClick</b> 

<img src="./img/MethodsAndWatch02.png" />

##### test 综合测试

```vue
<template>
  <div class="index-project">
    <ul>
      <li v-for="content in dataList">
        {{ content }}
      </li>
    </ul>
    <div class="book-sum">当前图书共计 {{ bookSum }} 本</div>
    <button @click="handleButton">添加图书</button>
  </div>
</template>

<script>
export default {
  name: "index",
  data() {
    return {
      dataList: [
        "Vue.js 从入门到精通",
        "Vue 3.x 入门指南",
        "Vue.js 2.x 实战",
        "React 全家桶",
        "React 入门指南",
        "你不知道的 JavaScript 实战技巧",
      ],
      addNewBook: "", // 用于存储点击事件中的内容
      isLock: false, // 设置节流锁, 防止重复添加, 默认为 false
    };
  },
  methods: {
    createBook() {
      if (this.isLock === true) return; // 设置节流锁, 防止重复添加
      this.isLock = true; // 设置节流锁, 防止重复添加, 上锁
      // 设置延时器, 2s 后将 addNewBook 添加到 dataList 中, 并解锁
      setTimeout(() => {
        this.dataList.push(this.addNewBook); // 将 addNewBook 添加到 dataList 中
        this.isLock = false; // 解锁
      }, 2000); // 2s 后执行
    },
    handleButton() {
      this.addNewBook = "JavaScript 悟道";
    },
  },
  computed: {
    bookSum() {
      return this.dataList.length;
    },
  },
  watch: {
    addNewBook(newVal) {
      if (newVal === "") return; // 如果输入框为空, 则不添加
      if (this.dataList.indexOf(newVal) !== -1) return; // 如果 datdList 中已存在该内容, 则不添加
      this.createBook();
    },
  },
};
</script>

<style lang="scss" scoped>
.index-project {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 100vh;
  background-color: #333;

  ul {
    color: white;
    font-size: 40px;

    li {
      display: flex;
      justify-content: center;
      align-items: center;
      margin-bottom: 20px;
    }
  }

  .book-sum {
    margin: 20px 0;
    color: white;
    font-size: 24px;
  }

  button {
    width: 220px;
    height: 60px;
    padding: 10px 20px;
    color: white;
    font-size: 24px;
    background-color: #409eff;
    border: none;
    outline: none;
    border-radius: 4px;
    cursor: pointer;
  }
}
</style>

```

​    <b style="color: #409EFF;">以上代码通过点击按钮后执行 methods 方法函数中的 handleButton 按钮点击事件函数, 内部执行将 data 中的 addNewBook 变量赋值操作, 为其赋上新值 "JavaScript 悟道", 然后函数结束. 但由于 add New Book 是 watch 监听属性的监听对象, 所以该属性被触发, 内部判断输入内容是否为空或重复数据, 如果不是则运行 methods 函数属性中的 createBook 函数, 在 createBook 函数中先判断是否被锁住, 如没有则开启节流, 并启用延时器, 在 2 秒后执行将 addNewBook 的值添加到 data 属性中的 dataList 中, 并解锁节流锁, 至此 createBook 函数结束, 且 watch 监听器完成监听任务.</b> 

##### summary 总结

​    <b style="color: #67C23A;">1. methods 可以在 watch 中调用且可以直接在 HTML 或 template 模板中使用, 而 watch 则不能被调用, 也不能直接在上述的 HTML 或 template 模板中使用.</b> 

​    <b style="color: #67C23A;">2. methods 函数属性的返回值比较自由, 可有可无. 但 watch 则默认负责处理比较耗时的操作, 且在操作完成后需要将值传递给需要的变量上, 不能将最终获取的值作为返回值进行返回. 但以上两个属性都可以为 data 数据的变化而进行对应的响应.</b> 

## 4. Vue 进阶

​    <b>本阶段将学习 表单处理、双向绑定、样式绑定方法等...</b> 

### A. 表单数据

​    <b>本小节将对表单的数据进行获取, 并在控制台输出</b> 

```vue
<template>
    <div class="index-project">
        <h1>Index 页面</h1>
        <section class="input-section">
            <div class="add-input">
                <label for="addInput">新增项：</label>
                <input
                    type="text"
                    id="addInput"
                    @input="handleInput"
                />
            </div>
            <button>提交</button>
        </section>
    </div>
</template>

<script>
export default {
    name: 'index',
    data() {
        return {

        }
    },
    methods: {
        // 事件处理函数
        handleInput(e) {
            console.log(e.target.value)
        },
    },
    computed: {},
    watch: {},
    created() { },
}
</script>

<style lang="scss" scoped>
// 项目外框
.index-project {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    color: white;
    background-color: #333333;

    // 项目标题
    h1 {
        flex: 1;
        font-size: 48px;
        margin: 20px 0;
    }

    // 项目输入部分
    .input-section {
        flex: 9;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 100%;
        box-sizing: border-box;

        // 新增项输入框
        .add-input {
            display: flex;
            align-items: center;
            justify-content: center;

            // 输入框标签
            label {
                margin-right: 10px;
                font-size: 36px;
            }

            // 输入框
            input {
                width: 360px;
                height: 36px;
                padding: 0 10px;
                font-size: 24px;
            }
        }

        // 提交按钮
        button {
            width: 120px;
            height: 36px;
            margin-top: 20px;
            font-size: 24px;
            background-color: #409EFF;
            color: white;
            padding: 4px 8px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            box-sizing: content-box;

            // 鼠标以上样式
            &:hover {
                background-color: #C6E2FF;
            }
        }
    }
}
</style>
```

​    <b>经过以上书写过后并使用命令行启动项目, 就会得到下方的页面.</b> 

<img src="./img/isInput.png" />

​    <b>接下来我们进行输入测试. 先测试数字 ( Number ) 类型</b> 

<img src="./img/inputNumber.png" />

​    <b>发现可以正常通过 input 元素输入触发 methods 函数属性中的 handleInput 函数, 并成功输出到控制台. 接下来测试 字符串 ( String ) 类型中的 Letter ( 字母 ).</b> 

<img src="./img/inputLetter.png" />

​    <b>通过以上发现感觉看着运行的还不错, 但很快就能发现一个问题, 那如果我还是输入一个 String ( 字符串 ) 类型的内容, 但我这次不输入字母了, 而是输入拼音会发生什么?</b> 

<img src="./img/inputChinese.png" />

​    <b>我们发现这样的话就发生只要输入就会触发事件, 由于中文拼音的缘故, 所以不能像英美那样去进行 input 事件. 这时就要设置: <i>compositionstart 事件</i> 和 <i>compositionend 事件</i> 这两个属性是在拼写状态下, 检查是否为组合成字符的属性, start 是开始组合, 直到组合结束会触发 end 结束事件. 那么为了可以使中文也能正常拼写显示, 所以将上方代码进行更改:</b>  

```vue
<template>
    <div class="index-project">
        <h1>Index 页面</h1>
        <section class="input-section">
            <div class="add-input">
                <label for="addInput">新增项：</label>
                <input
                    type="text"
                    id="addInput"
                    @input="handleInput"
                    @compositionstart="isLock = true"
                    @compositionend="isLock = false; handleInput($event)"
                />
            </div>
            <button>提交</button>
        </section>
    </div>
</template>

<script>
export default {
    name: 'index',
    data() {
        return {
            isLock: false, // 判断是否为输入状态的一个锁
        }
    },
    methods: {
        // 事件处理函数
        handleInput(e) {
            if (!this.isLock) console.log(e.target.value)
        },
    },
    computed: {},
    watch: {},
    created() { },
}
</script>

<style lang="scss" scoped>
// 项目外框
.index-project {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    color: white;
    background-color: #333333;

    // 项目标题
    h1 {
        flex: 1;
        font-size: 48px;
        margin: 20px 0;
    }

    // 项目输入部分
    .input-section {
        flex: 9;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 100%;
        box-sizing: border-box;

        // 新增项输入框
        .add-input {
            display: flex;
            align-items: center;
            justify-content: center;

            // 输入框标签
            label {
                margin-right: 10px;
                font-size: 36px;
            }

            // 输入框
            input {
                width: 360px;
                height: 36px;
                padding: 0 10px;
                font-size: 24px;
            }
        }

        // 提交按钮
        button {
            width: 120px;
            height: 36px;
            margin-top: 20px;
            font-size: 24px;
            background-color: #409EFF;
            color: white;
            padding: 4px 8px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            box-sizing: content-box;

            // 鼠标以上样式
            &:hover {
                background-color: #C6E2FF;
            }
        }
    }
}
</style>
```

​    <b>完成以上修改后就可以再次进行拼音输入测试了, 现在我们开始正常输入:</b> 

<img src="img/inputStart.png" />

<img src="img/inputEnd.png" />

​    <b>通过对控制台的观察, 我们发现它并没有对未拼写完成状态下的内容进行输出, 而是对最终输入完成的内容进行输出.</b> 

### B. 同步表单

​    <b>此处将对以上代码进行优化, 将输入的内容同步至 HTML 中, 并展示.</b> 

#### 1. 伪同步

​    <b>此处将使用 methods 函数方法对输入的内容进行同步, 虽然这并不是最优的解决方案. 具体做法就是将 input 元素通过 event 捕获当前触发事件元素, 并获取该元素的输入内容, 使用 e.target.value 对内容进行获取后, 并赋值到 data 中的 inputText 存储变量上, 最终在 HTML 中使用 `<textarea>{{ inputText }}</textarea>` 的方式进行展示.</b> 

```vue
<template>
    <div class="index-project">
        <h1>Index 页面</h1>
        <section class="input-section">
            <div class="input-wins">
                <div class="presentation-title">您输入的内容为:</div>
                <textarea
                    class="presentation-content"
                    :readonly="true"
                >{{ inputText }}</textarea>
            </div>
            <div class="add-input">
                <label for="addInput">新增项：</label>
                <input
                    type="text"
                    id="addInput"
                    @input="handleInput"
                    @compositionstart="isLock = true"
                    @compositionend="isLock = false; handleInput($event)"
                />
            </div>
            <button>提交</button>
        </section>
    </div>
</template>

<script>
export default {
    name: 'index',
    data() {
        return {
            isLock: false,
            inputText: '',
        }
    },
    methods: {
        // 事件处理函数
        handleInput(e) {
            if (!this.isLock) this.inputText = e.target.value;
        },
    },
    computed: {},
    watch: {},
    created() { },
}
</script>

<style lang="scss" scoped>
// 项目外框
.index-project {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    color: white;
    background-color: #333333;

    // 项目标题
    h1 {
        flex: 1;
        font-size: 48px;
        margin: 20px 0;
    }

    // 项目输入部分
    .input-section {
        flex: 9;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 100%;
        box-sizing: border-box;

        // 用户输入展示
        .input-wins {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            width: 538px;
            min-height: 47px;
            overflow: hidden;
            margin-bottom: 20px;

            // 展示标题
            .presentation-title {
                width: 100%;
                height: 47px;
                font-size: 36px;
                margin-bottom: 10px;
            }

            // 展示内容
            .presentation-content {
                width: 100%;
                min-height: 360px;
                font-size: 24px;
                box-sizing: border-box;
                padding: 10px;
                outline: none;
                resize: none;
                border-radius: 8px;
            }
        }

        // 新增项输入框
        .add-input {
            display: flex;
            align-items: center;
            justify-content: center;

            // 输入框标签
            label {
                margin-right: 10px;
                font-size: 36px;
            }

            // 输入框
            input {
                width: 360px;
                height: 36px;
                padding: 0 10px;
                font-size: 24px;
                outline: none;
                border-radius: 8px;
            }
        }

        // 提交按钮
        button {
            width: 120px;
            height: 36px;
            margin-top: 20px;
            font-size: 24px;
            background-color: #409EFF;
            color: white;
            padding: 4px 8px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            box-sizing: content-box;

            // 鼠标以上样式
            &:hover {
                background-color: #C6E2FF;
            }
        }
    }
}
</style>
```

​    <b>展示结果</b> 

<img src="img/SynchronousInput.png" />

#### 2. 问题 (1)

​    <b>虽然现在可以进行同步了, 但很快我们就又发现了一个新的问题, 这里我们添加一个 "重置" 按钮.</b> 

```vue
<template>
    <div class="index-project">
        <h1>Index 页面</h1>
        <section class="input-section">
            <div class="input-wins">
                <div class="presentation-title">您输入的内容为:</div>
                <textarea
                    class="presentation-content"
                    :readonly="true"
                >{{ inputText }}</textarea>
            </div>
            <div class="add-input">
                <label for="addInput">新增项：</label>
                <input
                    type="text"
                    id="addInput"
                    @input="handleInput"
                    @compositionstart="isLock = true"
                    @compositionend="isLock = false; handleInput($event)"
                />
            </div>
            <section class="btn-section">
                <button class="resetting"
                    @click="resetAdd"
                >重置</button>
                <button class="submit">提交</button>
            </section>
        </section>
    </div>
</template>

<script>
export default {
    name: 'index',
    data() {
        return {
            isLock: false,
            inputText: '',
        }
    },
    methods: {
        // 事件处理函数
        handleInput(e) {
            if (!this.isLock) this.inputText = e.target.value;
        },
        resetAdd() {
            this.inputText = '';
        },
    },
    computed: {},
    watch: {},
    created() { },
}
</script>

<style lang="scss" scoped>
@import './../setColor.scss';

// 项目外框
.index-project {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    color: white;
    background-color: #333333;

    // 项目标题
    h1 {
        flex: 1;
        font-size: 48px;
        margin: 20px 0;
    }

    // 项目输入部分
    .input-section {
        flex: 9;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 100%;
        box-sizing: border-box;

        // 用户输入展示
        .input-wins {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            width: 538px;
            min-height: 47px;
            overflow: hidden;
            margin-bottom: 20px;

            // 展示标题
            .presentation-title {
                width: 100%;
                height: 47px;
                font-size: 36px;
                margin-bottom: 10px;
            }

            // 展示内容
            .presentation-content {
                width: 100%;
                min-height: 360px;
                font-size: 24px;
                box-sizing: border-box;
                padding: 10px;
                outline: none;
                resize: none;
                border-radius: 8px;
            }
        }

        // 新增项输入框
        .add-input {
            display: flex;
            align-items: center;
            justify-content: center;

            // 输入框标签
            label {
                margin-right: 10px;
                font-size: 36px;
            }

            // 输入框
            input {
                width: 360px;
                height: 36px;
                padding: 0 10px;
                font-size: 24px;
                outline: none;
                border-radius: 8px;
            }
        }

        .btn-section {


            // 提交按钮
            button {
                width: 120px;
                height: 36px;
                margin-top: 20px;
                font-size: 24px;
                color: white;
                padding: 4px 8px;
                border: none;
                border-radius: 4px;
                cursor: pointer;
                box-sizing: content-box;

                // 除了: 最后一个按钮元素, 其余元素右边距20px
                &:not(:last-child) {
                    margin-right: 20px;
                }

                // 重置按钮样式
                &.resetting {
                    background-color: $bg-danger-base;

                    // 鼠标移上样式
                    &:hover {
                        background-color: $bg-danger-dark;
                    }
                }

                // 提交按钮样式
                &.submit {
                    background-color: $bg-brand-base;

                    // 鼠标移上样式
                    &:hover {
                        background-color: $bg-brand-dark;
                    }
                }

            }
        }
    }
}
</style>
```

​    <b>这时我们点击重置按钮, 就会发现一下问题.</b> 

<img src="img/reseting.png" />

<b>当我们点击按钮后问题就出来了, 它只重置了展示框的内容, 并没有对 Input 输入框产生效果.</b> 

<img src="img/resetingClick.png" />

<b>原因是 Input 输入框触发的是 @input 事件, 该事件只会将输入框中的内容同步到 data 存储数据属性中的 inputText 变量上, 再由 Vue 数据驱动视图的原则, 将 inputText 变量成功展示到带有 `{{ inputText }}` 的元素中. 所以将 inputText 清空后只会对使用该变量进行展示的视图产生影响, 而不会对 Input 输入框产生任何影响.</b> 

#### 3. 解决 (1)

​    <b>针对上方的问题需要将该元素进行绑定, 对 Input 元素使用 `:value="inputText"` 语法糖的方式或 `v-bind:value="inputText"` 全拼的方式进行数据绑定, 将 inputText 的值绑定到该元素上.</b> 

```vue
<template>
    <div class="index-project">
        <h1>Index 页面</h1>
        <section class="input-section">
            <div class="input-wins">
                <div class="presentation-title">您输入的内容为:</div>
                <textarea
                    class="presentation-content"
                    :readonly="true"
                >{{ inputText }}</textarea>
            </div>
            <div class="add-input">
                <label for="addInput">新增项：</label>
                <input
                    type="text"
                    id="addInput"
                    @input="handleInput"
                    @compositionstart="isLock = true"
                    @compositionend="isLock = false; handleInput($event)"
                    :value="inputText"
                />
            </div>
            <section class="btn-section">
                <button
                    class="resetting"
                    @click="resetAdd"
                >重置</button>
                <button class="submit">提交</button>
            </section>
        </section>
    </div>
</template>

<script>
export default {
    name: 'index',
    data() {
        return {
            isLock: false,
            inputText: '',
        }
    },
    methods: {
        // 事件处理函数
        handleInput(e) {
            if (!this.isLock) this.inputText = e.target.value;
        },
        resetAdd() {
            this.inputText = '';
        },
    },
    computed: {},
    watch: {},
    created() { },
}
</script>

<style lang="scss" scoped>
@import './../setColor.scss';

// 项目外框
.index-project {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    color: white;
    background-color: #333333;

    // 项目标题
    h1 {
        flex: 1;
        font-size: 48px;
        margin: 20px 0;
    }

    // 项目输入部分
    .input-section {
        flex: 9;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 100%;
        box-sizing: border-box;

        // 用户输入展示
        .input-wins {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            width: 538px;
            min-height: 47px;
            overflow: hidden;
            margin-bottom: 20px;

            // 展示标题
            .presentation-title {
                width: 100%;
                height: 47px;
                font-size: 36px;
                margin-bottom: 10px;
            }

            // 展示内容
            .presentation-content {
                width: 100%;
                min-height: 360px;
                font-size: 24px;
                box-sizing: border-box;
                padding: 10px;
                outline: none;
                resize: none;
                border-radius: 8px;
            }
        }

        // 新增项输入框
        .add-input {
            display: flex;
            align-items: center;
            justify-content: center;

            // 输入框标签
            label {
                margin-right: 10px;
                font-size: 36px;
            }

            // 输入框
            input {
                width: 360px;
                height: 36px;
                padding: 0 10px;
                font-size: 24px;
                outline: none;
                border-radius: 8px;
            }
        }

        .btn-section {


            // 提交按钮
            button {
                width: 120px;
                height: 36px;
                margin-top: 20px;
                font-size: 24px;
                color: white;
                padding: 4px 8px;
                border: none;
                border-radius: 4px;
                cursor: pointer;
                box-sizing: content-box;

                // 除了: 最后一个按钮元素, 其余元素右边距20px
                &:not(:last-child) {
                    margin-right: 20px;
                }

                // 重置按钮样式
                &.resetting {
                    background-color: $bg-danger-base;

                    // 鼠标移上样式
                    &:hover {
                        background-color: $bg-danger-dark;
                    }
                }

                // 提交按钮样式
                &.submit {
                    background-color: $bg-brand-base;

                    // 鼠标移上样式
                    &:hover {
                        background-color: $bg-brand-dark;
                    }
                }

            }
        }
    }
}
</style>
```

<b>这里再次输入 "Hello World", 并点击 "重置" 按钮</b> 

<img src="img/reseting.png" />

<b>点击按钮后发现: 全部都被重置.</b> 

<img src="img/resetingClickBind.png" />

<b>原因是: 两项都被以不同形式绑定了 inputText 变量, 所以后期点击重置后两个框内的内容都被清空了. 这也是 Vue 数据驱动视图的好处.</b> 

### C. v-modle 数据绑定

​    <b>在上面我们虽然实现了数据的绑定, 但还是过于繁琐且会出现一些其他问题. 介于以上问题 Vue 官方提供了一个更方便的属性: `v-modle=""` 属性. 可用于实现数据的双向绑定.</b> 

```vue
<template>
    <div class="index-project">
        <h1>Index 页面</h1>
        <section class="input-section">
            <div class="input-wins">
                <div class="presentation-title">您输入的内容为:</div>
                <textarea
                    class="presentation-content"
                    :readonly="true"
                >{{ inputText }}</textarea>
            </div>
            <div class="add-input">
                <label for="addInput">新增项：</label>
                <input
                    type="text"
                    id="addInput"
                    v-model="inputText"
                />
            </div>
            <section class="btn-section">
                <button
                    class="resetting"
                    @click="resetAdd"
                >重置</button>
                <button class="submit">提交</button>
            </section>
        </section>
    </div>
</template>

<script>
export default {
    name: 'index',
    data() {
        return {
            isLock: false,
            inputText: '',
        }
    },
    methods: {
        resetAdd() {
            this.inputText = '';
        },
    },
    computed: {},
    watch: {},
    created() { },
}
</script>

<style lang="scss" scoped>
@import './../setColor.scss';

// 项目外框
.index-project {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    color: white;
    background-color: #333333;

    // 项目标题
    h1 {
        flex: 1;
        font-size: 48px;
        margin: 20px 0;
    }

    // 项目输入部分
    .input-section {
        flex: 9;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 100%;
        box-sizing: border-box;

        // 用户输入展示
        .input-wins {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            width: 538px;
            min-height: 47px;
            overflow: hidden;
            margin-bottom: 20px;

            // 展示标题
            .presentation-title {
                width: 100%;
                height: 47px;
                font-size: 36px;
                margin-bottom: 10px;
            }

            // 展示内容
            .presentation-content {
                width: 100%;
                min-height: 360px;
                font-size: 24px;
                box-sizing: border-box;
                padding: 10px;
                outline: none;
                resize: none;
                border-radius: 8px;
            }
        }

        // 新增项输入框
        .add-input {
            display: flex;
            align-items: center;
            justify-content: center;

            // 输入框标签
            label {
                margin-right: 10px;
                font-size: 36px;
            }

            // 输入框
            input {
                width: 360px;
                height: 36px;
                padding: 0 10px;
                font-size: 24px;
                outline: none;
                border-radius: 8px;
            }
        }

        .btn-section {


            // 提交按钮
            button {
                width: 120px;
                height: 36px;
                margin-top: 20px;
                font-size: 24px;
                color: white;
                padding: 4px 8px;
                border: none;
                border-radius: 4px;
                cursor: pointer;
                box-sizing: content-box;

                // 除了: 最后一个按钮元素, 其余元素右边距20px
                &:not(:last-child) {
                    margin-right: 20px;
                }

                // 重置按钮样式
                &.resetting {
                    background-color: $bg-danger-base;

                    // 鼠标移上样式
                    &:hover {
                        background-color: $bg-danger-dark;
                    }
                }

                // 提交按钮样式
                &.submit {
                    background-color: $bg-brand-base;

                    // 鼠标移上样式
                    &:hover {
                        background-color: $bg-brand-dark;
                    }
                }

            }
        }
    }
}
</style>
```

​    <b>此处使用了 `v-modle` 属性, 并将它绑定的目标设置为: "inputText" 变量, 再将 methods 函数属性中的 handleInput 函数删除. 且功能也并没有出现任何问题, 依旧可以正常运行.</b> 

#### 1. smmary 总结

​    <b>使用 `v-model` 双向绑定可以将: <span style="color: #E6A23C; text-decoration: underline;">输入框</span> 与 <span style="color: #E6A23C; text-decoration: underline;">data 中的数据</span> 进行绑定, 且大大节省了使用 @input 和 `bind:value=""` 的代码量.</b>

### D. 绑定表单控件

​    <b>上方提供了一个新的 `v-modle` 绑定属性, 那么这里来看一下它除了可以对输入框的内容进行绑定外还能做些什么...</b> 

#### 1. 绑定单选框

​    <b>该部分将对单选框进行绑定.</b> 

