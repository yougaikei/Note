# Vue + Types

​    <b>本文档将会对 Vue 与 TypeScript 的应用进行更深层次的讲解说明.</b> 

## 1. 创建项目

​    <b>使用下方代码对项目进行构建</b> 

```npm
npm init vue@latest
```

​    <b>在创建的过程中可能会需要对控制台进行操作, 问题大致如下:</b> 

<b>1. 是否安装 TypeScript 选项?</b> 

```txt
√ Add TypeScript? ... No/Yes
```

<b>2. 是否安装 JSX 插件?</b> 

```txt
√ Add JSX Support? ... No/Yes
```

<b>3. 是否安装 VueRouter ( Vue 路由 ) 插件?</b> 

```txt
√ Add Vue Router for Single Page Application development? ... No / Yes
```

<b>4. 是否安装 Pinia ( Vue 状态管理库 )插件?</b> 

```txt
√ Add Pinia for state management? ... No/Yes
```

<b>5. 是否安装 Vitest ( Jest Vue 版测试单元 ) 插件?</b> 

```txt
√ Add Vitest for Unit Testing? ... No / Yes
```

<b>6. 是否添加 End-to-End（E2E）测试解决方案?</b> 

```txt
√ Add an End-to-End Testing Solution? ... No/Yes
```

<b>7. 是否添加 EsLint 代码校验工具?</b> 

```txt
√ Add ESLint for code quality? ... No / Yes
```

<b>8. 是否添加 Prettier 代码格式化工具?</b> 

```txt
√ Add Prettier for code formatting? ... No / Yes
```

<b>例  图:</b> 

![NpmInit](D:\MyTable\Git\Note\components\Vue\img\NpmInit.png)

## 2. 初始化项目

​    <b>经过上述的操作就会得到一份 Vue + Ts ( TypeScript) + EsLint 的项目初始文件. 创建完毕后就可以使用 cmd 命令进行下载依赖并且在 VsCode ( Visual Studio Code ) 中打开了.</b> 

```cmd
cd ts-note & npm i & code ./
```

<b style="color: red;">温馨提示: 以上内容中的 `ts-note` 是项目名称, 后期需要替换成自己的项目名称.</b> 

​    <b>打开后就可以在 VsCode 中看到已经生成好的项目了, 接下来我们需要对项目进行后期配置. (<span style="color: red;">个人比较倾向于使用 stylus, 所以会在项目中对其进行下载并安装</span>)</b> 

<b>例  图:</b> 

![NpmInit](D:\MyTable\Git\Note\components\Vue\img\NpmInit.png)

<b>1. 删除不必要的文件</b> 

​    <b>1) 删除 `src/assets` 目录下的 `base.css` 文件</b>  

​    <b>2) 删除 `src/components` 目录下的所有文件</b> 

<b style="color: red;">经过以上操作后还需要对引用它们的地方进行操作, 对 `src/assets` 目录下的 `main.css` 文件进行内容清空, 其次对 `src/App.vue` 文件进行清空并重构.</b> 

<b>2. 因个人喜好所以本教程将使用 stylus 和 stylus-loader 样式插件.</b> 

​    <b>1). 下载插件</b> 

```npm
npm i stylus stylus-loader -D

// 或 ( Or )

yarn add stylus stylus-loader -D

```

<b>3. 对 EsLint 进行配置, 在项目根目录中新建一个 `.eslintignore` 文件, 该文件是用于保存不需要 EsLint 去对其进行检测的文件类型.</b> 

```.eslintignore
node_modules/
dist/
build/
coverage/
*.log
*.min.js
*.min.css
*.svg
*.png
*.jpg
*.jpeg
*.gif

```

​    <b>1) 配置完成后继续修改 EsLint 的配置文件 ( `.eslintrc.cjs` ).</b> 

```cjs
/* eslint-env node */
require('@rushstack/eslint-patch/modern-module-resolution')

module.exports = {
  root: true,
  'extends': [
    'plugin:vue/vue3-essential',
    'eslint:recommended',
    '@vue/eslint-config-typescript'
  ],
  parserOptions: {
    ecmaVersion: 'latest'
  }
}

```

​        <b>对上方初始化后的文件新增一些内容.</b> 

```cjs
/* eslint-env node */
require('@rushstack/eslint-patch/modern-module-resolution')

module.exports = {
    root: true,
    
    // +++++ 新增规则- 01 +++++
    // 新增基础配置
    env: {
        // 可以在 Node 中运行
        node: true,
        // 可以在浏览器中运行
        browser: true,
        // 允许使用 es2020
        es2020: true
    },
    // +++++ 结束 - 01 +++++
    
    'extends': [
        'plugin:vue/vue3-essential',
        'eslint:recommended',
        '@vue/eslint-config-typescript'
    ],
    parserOptions: {
        ecmaVersion: 'latest'
    },
    
    // +++++ 新增内容 -02 +++++
    // 新增规则
    rules: {
        // 最后一个属性或数组元素后面的逗号取消
        'comma-dangle': ['error', 'never'],
        // 禁止使用分号
        'semi': ['error', 'never'],
        // 禁止使用var
        'no-var': 'error',
        // 代码书写完毕后需要留白一行
        'eol-last': ['error', 'always'],
        // 所有 tab 均为 4 个空格
        'indent': ['error', 4],
        // 所有属性均使用单引号
        'quotes': ['error', 'single'],
        // Vue3 中的 template 中的属性使用单引号
        'vue/html-quotes': ['error', 'single'],
        // Vue3 Tab 使用 4 个空格
        'vue/html-indent': ['error', 4]
    }
    // +++++ 结束 - 02 +++++
}

```

<b>4. 新增 postcss 以及 tailwindcss ( 样式兼容 和 tailwind 样式 )</b>

​    <b>1) 下载以上插件</b> 

```npm
npm i tailwindcss postcss autoprefixer postcss-import -D

// 或 ( Or )

yarn add tailwindcss postcss autoprefixer postcss-import -D

```

​    <b>2) 配置 postcss 样式兼容化的配置文件 (postcss.config.cjs ), 在根目录下新建一个 `postcss.config.cjs` 文件并对其进行配置书写.</b> 

```cjs
module.exports = {
    plugins: [
        require('postcss-import'),
        require('tailwindcss'),
        require('autoprefixer')
    ]
}

```

​    <b>3) 配置 tailwindcss 样式的配置文件 ( tailwind.config.js )</b> 

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
    content: [
        // +++++ 新增内容 - 01 +++++
        './index.html',
        './src/**/*.{vue,js,ts,jsx,tsx}'
        // +++++ 结束 - 01 +++++
    ],
    theme: {
        extend: {}
    },
    plugins: []
}

```

<b>4. 对 `tsconfig.json` 和 `vite.config.ts` 进行路径别名的配置操作.</b> 

​    <b>1) 对 `tsconfig.json` 进行路径别名的配置</b>

```json
{
  "files": [],
  "references": [
    {
      "path": "./tsconfig.node.json"
    },
    {
      "path": "./tsconfig.app.json"
    }
  ],
    
  // +++++ 新增部分 -01 +++++
  // 设置路径别名
  "compilerOptions": {
    "baseUrl": "./",
    "paths": {
      "@/*": ["src/*"],
      "@/components/*": ["src/components/*"],
      "@/views/*": ["src/views/*"],
      "@/assets/*": ["src/assets/*"],
      "@/widgets/*": ["src/widgets/*"]
    }
  }
  // +++++ 结束 - 01 +++++
}

```

​    <b>2) 对 `vite.config.ts` 文件进行配置</b> 

```ts
import { fileURLToPath, URL } from 'node:url'
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

// https://vitejs.dev/config/
export default defineConfig({
    plugins: [vue()],
    resolve: {
        alias: {
            '@': fileURLToPath(new URL('./src', import.meta.url)),
            
            // +++++ 新增部分 - 01 +++++
            '@components': fileURLToPath(new URL('./src/components', import.meta.url)),
            '@views': fileURLToPath(new URL('./src/views', import.meta.url)),
            '@widgets': fileURLToPath(new URL('./src/widgets', import.meta.url)),
            '@assets': fileURLToPath(new URL('./src/assets', import.meta.url))
            // +++++ 结束 - 01 +++++
        }
    }
})

```

<b>5. 对 `env.d.ts` 新增模块对象, 并告诉编译器如何解析 Vue 文件. 由于 Vue 是一个单文件组件, 包含了模板、脚本和样式, 所以在 TypeScript 项目中需要特殊的声明方式</b> 

```ts
/// <reference types="vite/client" />

// +++++ 新增内容 - 01 +++++
declare module '*.vue' {
    import type { DefineComponent } from 'vue'
    const vueComponent: DefineComponent<{}, {}, any>
    export default vueComponent
}
// +++++ 结束 - 01 +++++

```

## 3.  Ref 类型

​    <b>本章讲解 Ref 类型的定义方式</b> 

```vue
<template>
    <div class='w-9/12 mx-auto ref-type'>
        <h2 class='text-5xl mb-5 flex font-blod'>
            1. RefType 测试
        </h2>
        <section>
            <div class="ml-12 text-4xl mb-5">
                <p>count1: {{ count1 }}</p>
                <p>count2: {{ count2 }}</p>
                <p>count3: {{ count3 }}</p>
            </div>
        </section>
    </div>
</template>

<script setup lang="ts">
import { ref, type Ref } from 'vue'

// 在 vue + ts 情况下定义 Ref 类型

// No.01 不做任何改变, 直接定义
const count1 = ref(0)

// No.02 使用泛型 - ( 1 )
// 直接使用 ref<type> 进行定义
const count2: Ref<number> = ref(0)

// No.03 使用泛型 - ( 2 )
// 直接使用 ref<type> 进行定义
const count3 = ref<number>(0)


</script>

<style lang="stylus" scoped></style>

```

