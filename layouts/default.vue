<template>
  <div>
    <side-bar></side-bar>
    <Nuxt />
  </div>
</template>

<style lang="less">
@import "~@/styles/reset.less";
html {
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

body {
  --background-color: #f9f9f9;
  --sidebar-background-color: #fff;
  --sidebar-border-color: #e9e9e9;
  --text-color: #333;
  --menu-item-background: #f7f7f7;
  font-size: 1.6rem;

  color: var(--text-color);
  background: var(--background-color);
}

a {
  color: var(--text-color);
}

.dark--theme {
  --text-color: #eee;
  --background-color: #282d3a;
  --sidebar-background-color: rgba(0, 0, 0, 0.1);
  --sidebar-border-color: rgba(255, 255, 255, 0.1);
  --menu-item-background: rgba(255, 255, 255, 0.1);
}

.row {
  display: flex;
  margin: 0 -5px;
}

.row--center-v {
  align-items: center;
}

.column {
  flex: 1;
  padding: 5px;
}

.column--wrap {
  flex: none;
}
</style>
