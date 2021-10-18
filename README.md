# Modern CSS Layout

正在玩命完善中，进度 60%，预计 10 月 20 日完工...

## 特点

- 使用 CSS 自定义属性，方便覆盖修改
- 使用 Grid 布局，性能更好。（在使用之前，请注意你需要兼容的浏览器，如果不兼容请放弃）
- 提供常见布局的在线 DEMO

## 说明

- `ml` 缩写表示 modern layout
-

```css
/* 
* ml 为 modern layout 的缩写
*/

:root {
  --ml-width: 1200px; /* 固定宽度与最大宽度的取值 */
  --ml-min-width: 1200px; /* 最小宽度 */
  --ml-min-height: 100vh; /* 最小高度 */
  --ml-header-height: 60px; /* header 高度 */
  --ml-header-z-index: 5000; /* header z-index */
  --ml-aside-left-width: 300px; /* 左边栏宽度 */
  --ml-aside-right-width: 300px; /* 右边栏宽度 */
}

/* 内容水平居中设计，默认设置 max-width */
.ml-center {
  max-width: var(--ml-width);
  margin-left: auto;
  margin-right: auto;
}

/* 
* 左边栏布局
* 边栏宽度固定
* 内容宽度为除掉边栏宽度后的剩余容器宽度
*/
.ml-left-aside {
  display: grid;
  grid-template-columns: var(--aside-left-width) 1fr;
}

/* 
* 右边栏布局
* 右边栏宽度固定
* 内容宽度为除掉边栏宽度后的剩余容器宽度
*/
.ml-right-aside {
  display: grid;
  grid-template-columns: 1fr var(--aside-right-width);
}

/* 
* 左右边栏布局
* 左右边栏宽度固定
* 内容宽度为除掉边栏宽度后的剩余容器宽度
*/
.ml-both-aside {
  display: grid;
  grid-template-columns: var(--aside-left-width) 1fr var(--aside-left-width);
}

/* 
* fixed 或 sticky 顶部
*/
.ml-fixed-header {
  position: fixed;
  left: 0;
  top: 0;
  right: 0;
  height: var(--ml-header-height);
  z-index: var(--ml-header-z-index);
}

.ml-header--sticky {
  position: sticky;
  height: var(--ml-header-height);
  z-index: var(--ml-header-z-index);
}

/*
* 固定宽度布局
* ml-content 父级元素，挂一个 ml-min-width 即可实现固定宽度布局
* 条件：var(--ml-min-width) >= var(--ml-width)
*/
.ml-min-width {
  min-width: var(--ml-min-width);
}

/*
* 最小高度布局
* 适用于有个底部，内容再少，也可以撑开全屏
*/
.ml-min-height {
  display: grid;
  min-height: var(--ml-min-height);
  grid-template-rows: 1fr auto; /* 底部高度为 auto， 剩余全是内容高度 */
}

/* 固定左边栏 */
.ml-fixed-aside {
  position: fixed;
  top: var(--ml-header-height);
  bottom: 0;
  left: 0;
  width: var(--ml-aside-left-width);
}

/*
* 固定顶部和左边栏布局
*/
.ml-main-without-aside-header {
  margin-left: var(--ml-aside-left-width);
  margin-top: var(--ml-header-height);
  height: calc(100vh - var(--ml-header-height));
  overflow-y: auto;
}
```
