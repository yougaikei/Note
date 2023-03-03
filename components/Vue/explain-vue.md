# VueProject

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
    props: {},
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

### F. 计算属性

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
    props: {},
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

### G. 函数属性

​    <b>Vue 除了提供计算也提供了 ( methods ) 函数属性, 多用于: 表单验证、Ajax 数据传递、事件函数等, 且在 Vue 中的 `methods` 内部定义函数的好处是可以直接使用 `this.` 的形式访问到 Vue 中 ` data()` 函数内所定义的数据. 且构思清晰减少 HTML 代码量, 并且还可以进行复用.</b>  

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
    props: {},
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

.

