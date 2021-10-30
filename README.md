# ts-vue2.0-element

### 说明

#### 关于 package.json
```js
"dependencies": {
    "vue-class-component": "^7.2.3",  // 提供使用 Class 语法写 Vue 组件
    "vue-property-decorator": "^9.1.2", // 在 Class 语法的基础之上提供了一些辅助装饰
}
"devDependencies": {
    "@typescript-eslint/eslint-plugin": "^4.18.0",  // 使用 ESlint 校验 TS 语法
    "@typescript-eslint/parser": "^4.18.0", // 将 TS 转换成 AST 供 ESlint 校验使用
    "@vue/cli-plugin-typescript": "~4.5.0", // 一个 ts ts-loader fork-ts-checker-webpack-plugin 的集合 实现更快的校验
    "@vue/eslint-config-typescript": "^7.0.0",  // 兼容 eslint 的 ts 校验规则
    "typescript": "~4.1.5", // TS 编译器 提供类型校验和转换JS功能
  }

```

#### 关于 src/shims-vue.d.ts src/shims-tsx.d.ts
- 为了让 ts 识别 .vue 文件 一般不用动它
- 使用 jsx 时的补充声明 如果没有使用 jsx 可以忽略

#### ES6 语法的装饰器 就是方便的拓展 Class 的定义 
- 这个语法是草案阶段 估计会有大的改动 不建议使用
```js
function testable(target) {
    target.isTestable = true;
}

@testable
class MyClass {};


MyClass.isTestable;  // true
```

#### TS 创建组件的方式 
- 1. Options APIs
```js
import vue from 'vue'
export default vue.extends({
    data () {
        return {
            a: 234
        }
    }
    methods: {
        increment() {
            this.a ++
        }
    }
})
```
- 2. Class APIs
```js
import Vue form 'vue'
import Component from 'veu-class-component'

@Component
export default class Counter extends Vue {
    const a = 234
    increment () {
        this.a ++
    }
}
```
- 3. Class APIs + decorator() (不建议使用)
```js
import { Vue, Component, Prop } from 'vue-property-decorator'

@component
export default class YourComponent extends Vue {
    @Prop(Number) readonly propA: number | undefined

}
```
> 建议 No Class APIs , 只用 Options APIs
- class 语法只是一种写法而已 最终还是要转换成普通的数据结构
- 装饰器语法没有正式发布 建议了解就可以



