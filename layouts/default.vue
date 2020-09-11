<template>
  <div>
    <side-bar></side-bar>
    <Nuxt />
  </div>
</template>

<style lang="less">
@import "~@/styles/reset.less";
html {
  font-family: "Montserrat", sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

body {
  font-size: 62.5%;
  --background-color: #f9f9f9;
  --sidebar-background-color: #fff;
  --sidebar-border-color: #e9e9e9;
  --sidebar-width: 300px;
  --text-color: #444;
  --menu-item-background: #f7f7f7;
  --workload-item-background: rgba(0, 0, 0, 0.03);
  --progress-border-color: #eee;
  --filter-input--background: #fff;
  --filter-input--border-color: #efefef;
  --filter-input--border-color--hover: #ccc;
  --filter-input--border-color--focus: #999;
  --th-border-color: #d9d7d7;

  font-size: 1.6rem;

  color: var(--text-color);
  background: var(--background-color);
  padding-left: var(--sidebar-width);
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
  --workload-item-background: rgba(255, 255, 255, 0.1);
  --progress-border-color: #3e434e;
  --filter-input--background: rgba(255, 255, 255, 0.1);
  --filter-input--border-color: transparent;
  --filter-input--border-color--hover: rgba(255, 255, 255, 0.1);
  --filter-input--border-color--focus: rgba(255, 255, 255, 0.2);
  --th-border-color: rgba(255, 255, 255, 0.2);
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

.page {
  padding: 50px 0;
}

.page__title {
  font-size: 45px;
  font-weight: 800;
}

.page__header {
  padding-bottom: 50px;
}

.container {
  width: 90%;
  max-width: 1280px;
  margin: 0 auto;
}

.form-input {
  padding: 8px;
  border-radius: 2px;
  border: 1px solid #efefef;
  background: #fff;
  -webkit-transition: all 0.3s ease;
  transition: all 0.3s ease;
  font-size: 14px;
  font-family: Montserrat, sans-serif;
  outline: none;

  &:hover {
    border-color: #ccc;
  }

  &:active,
  &:focus {
    border-color: #777;
  }
}

.form-input--wide {
  width: 300px;
}

.table {
  width: 100%;
}

.button--action {
  width: 30px;
  height: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  border: none;
  border-radius: 4px;
  transition: all ease 0.3s;
  cursor: pointer;
  outline: none;
  background: transparent;
  padding: 0;
  transition: all ease 0.3s;
  color: var(--text-color);

  &:hover:not([disabled]) {
    background: rgba(0, 0, 0, 0.1);
  }
}

.button--action__icon {
  width: 20px;
  height: auto;
  display: block;
}

.button--action:disabled {
  opacity: 0.4;
  cursor: default;
}
</style>
