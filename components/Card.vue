<template>
  <div class="card">
    <slot></slot>
  </div>
</template>

<script>
export default {

};
</script>

<style lang="less" scoped>
.card {
  background: var(--sidebar-background-color);
  border-radius: 5px;
  overflow: hidden;
  -webkit-box-shadow: 0 5px 10px -7px rgba(0, 0, 0, 0.3);
  box-shadow: 0 5px 10px -7px rgba(0, 0, 0, 0.3);
}
</style>
