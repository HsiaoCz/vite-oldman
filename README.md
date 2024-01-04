# Vue 3 + TypeScript + Vite

This template should help get you started developing with Vue 3 and TypeScript in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Type Support For `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin) to make the TypeScript language service aware of `.vue` types.

If the standalone TypeScript plugin doesn't feel fast enough to you, Volar has also implemented a [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669) that is more performant. You can enable it by the following steps:

1. Disable the built-in TypeScript Extension
   1. Run `Extensions: Show Built-in Extensions` from VSCode's command palette
   2. Find `TypeScript and JavaScript Language Features`, right click and select `Disable (Workspace)`
2. Reload the VSCode window by running `Developer: Reload Window` from the command palette.

npm run dev

public 下面的存放的是静态资源
这里的静态资源 不会被编译

src 下面也 assets 存放的静态资源 图片什么的
components 下面存放的是组件文件

app.vue 全局入口文件
main.ts 全局的 ts 文件 全局样式都可以在这个里面引入 或者是全局的 API 配置
vite-env.d.ts 主要是让 ts 认识一下 vue

index.html 入口文件
package.json 配置文件 命令
tsconfig.json ts 配置文件

每个组件 有三部分组成

script 主要是逻辑 js 代码 model 里面只能使用一个 setup 语法糖
template 写标签的 view
style 写样式 css 的

npm run dev 会去找 package.json 里面的 dev 命令
会调用 vite 命令，但是如果我们直接使用 vite，是不好使的

**vue 的模板语法**

选项式 api

```javascript
export default {
  data() {
    return {
      age: 18,
    };
  },
  methods: {
    xxx() {},
  },
};
```

setup 函数模式

```javascript
export default{
   setup(){
      const a=1
      return {
         a
      }
   }
}

// 这种定义的必须手动return出去
<script setup lang="ts">
   const a:number =1
</script>

// 这种定义不需要手动return
```

模板语法

```html
<template>
  模板里面可以直接运算
  <div>{{ a }}</div>
</template>
```

v-text

展示到div里面
```typescript
<template>
  <div v-text="a">

  </div>
</template>
<script>
const a:string="我是一段文字xxxx"
</script>
```

v-html 也可以展示文字 但是这种展示还支持标签
但是不支持组件
```typescript
<template>
  <div v-html="a">

  </div>
</template>
<script>
const a:string="<section style="color:red">我是一段文字xxxx</section>"
</script>
```

v-if 可以判断值 值为真可以显示
值为假不显示 原理是通过删除标签来控制其显示的
将整个元素 变成注释节点
```typescript
<template>
  <div v-if="b">
     true
  </div>
</template>
<script>
const a:string="<section style="color:red">我是一段文字xxxx</section>"
const b:boolean=true
</script>
```

v-show 也可以展示 用法一样
但是原理不同 v-show 通过控制标签的display属性来控制显示

```typescript
<template>
  <div v-show="b">
     true
  </div>
</template>
<script>
const a:string="<section style="color:red">我是一段文字xxxx</section>"
const b:boolean=true
</script>
```

v-else v-else-if

```typescript
<template>
  <div v-if="a=='A'">
     true
  </div>
  <div v-else-if="a=='C'">
  </div>
  <div v-else="a=='B'">
     false
  </div>
</template>
<script>
const a:string="<section style="color:red">我是一段文字xxxx</section>"
const b:boolean=true
</script>
```
