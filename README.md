# t-vue-scroll-top

## Module Usage

```bash
npm i t-vue-scroll-top
```

#### 

#### demo.vue

```vue
<template>
    <div id="app">
        <ScrollTop />
        <div>lorem500</div>
    </div>
</template>

<script>
    
import ScrollTop from 't-vue-scroll-top';

export default {
    name: 'App',   
    components: {
         ScrollTop,
    },
};
</script>
```



#### shims-vue.d

套件使用vue + ts寫， 安裝引入會有找不到module的錯誤，套件暫時找不到方法解決，暫提供短解：在shims-vue.d 加入 declare module "t-vue-scroll-top";

```typescript
declare module "*.vue" {
  import Vue from "vue";
  export default Vue;
}

declare module "t-vue-scroll-top";

```



## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

## Other Notes

1. [npm url](https://www.npmjs.com/package/t-vue-scroll-top)
2. [demo](https://7070587.github.io/vue-scroll-top/)