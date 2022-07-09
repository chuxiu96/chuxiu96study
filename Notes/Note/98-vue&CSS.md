## vue项目引入全局样式

现在有一个index.css文件，想项目中所有的vue文件不需要导包就可以使用其中的样式。实现方式有3种：

### 1 - 在 App.vue 的style标签内引入

```vue
<style lang="less">
@import url('./css/index.css');
// or
@import './css/index.css';
</style>
```

### 2 - 在 main.js 中引入

```js
// 引入全局样式
import './css/index.css';
```

### 3 - 项目根目录下的 index.html 的 style 中引入

```html
<style>
    /* 样式代码 */
</style>
```

