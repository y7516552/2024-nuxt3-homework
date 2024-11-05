# Nuxt3每日任務進度

| Day |進度|
| --- |---|
|11/4| 起手式 : 建立 Nuxt3 專案|
|11/5| Nuxt3 專案引入 CSS 樣式 |


## Day1 建立 Nuxt3 專案

### 步驟一

```bash
npx nuxi@latest init [專案名稱]
```

### 步驟二

```bash
npx nuxi add page index
```

### 步驟三

在 `app.vue` 中加入`<NuxtPage/>` 

```html
// app.vue

<template>
  <NuxtRouteAnnouncer />
  <!-- <NuxtWelcome /> -->
  <NuxtPage/>
</template>
```


## Day2 專案引入 CSS 樣式

### 步驟一

加入Sass、bootstrap
```bash
npm install sass@1.70.0
npm install bootstrap@5.3.3
```


### 步驟二

1. 在根目錄下新增assets 資料夾
2. 在assets 資料夾中新增 stylesheets 資料夾
3. 在stylesheets 資料夾中 新增 all.scss 

```scss
// assets/stylesheets/all.scss

@import "bootstrap/scss/functions";

@import "bootstrap/scss/variables";
@import "bootstrap/scss/variables-dark";

@import "bootstrap/scss/maps";
@import "bootstrap/scss/mixins";
@import "bootstrap/scss/root";

@import "bootstrap/scss/utilities";
@import "bootstrap/scss/reboot";
@import "bootstrap/scss/containers";

@import "bootstrap/scss/buttons";

@import "bootstrap/scss/utilities/api";
```


### 步驟三

設定 nuxt.config.ts

```tsx
// nuxt.config.ts
export default defineNuxtConfig({
	//... 其他設定
  css: [
    '@/assets/stylesheets/all.scss', 
  ],
})
```

### 步驟四

在stylesheets 資料夾中 新增 _variables.scss

```scss
// assets/stylesheets/_variables.scss

$fs-base: 1rem;

$fs-sm: $fs-base * 0.875;
$fs-md: $fs-base * 1.5;
$fs-lg: $fs-base * 2;
$fs-xl: $fs-base * 2.5;
```

### 步驟五

在 nuxt.config.ts 設定 vite 選項的 [](https://www.notion.so/709ddedc0e42419dba6f8dae377e9db8?pvs=21)[css.preprocessorOptions.scss.additionalData](https://vitejs.dev/config/shared-options.html#css-preprocessoroptions-extension-additionaldata) 。

```tsx

// nuxt.config.ts
export default defineNuxtConfig({
  //... 其他設定
  vite: {
    css: {
      preprocessorOptions: {
        scss: {
          additionalData: `
            @import "@/assets/stylesheets/_variables.scss"; // 在全部的元件都引入 _variables.scss
          `,
        },
      },
    },
  },
});

```

