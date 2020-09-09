<template>
  <nuxt-link to="/" class="menu-item">
    <div>
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-bar-chart menu-item__icon">
        <line x1="12" y1="20" x2="12" y2="10"></line>
        <line x1="18" y1="20" x2="18" y2="4"></line>
        <line x1="6" y1="20" x2="6" y2="16"></line>
      </svg>
    </div>
    <div class="menu-item__label">
      {{ title }}
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: 'MenuItem',
  props: {
    title: {
      type: String,
      default: '',
    },
  },
};
</script>

<style lang="less" scoped>
.menu-item {
  display: flex;
  align-items: center;
  height: 32px;
  border-radius: 4px;
  transition: all ease 0.3s;
  padding: 10px;
  cursor: pointer;
  margin-bottom: 2px;
  text-decoration: none;

  &:hover {
    background-color: var(--menu-item-background);
  }
}

.menu-item__icon {
  margin-right: 10px;
  display: block;
  height: auto;

  &.feather {
    width: 18px;
  }
}

.menu-item__label {
  font-size: 14px;
  font-weight: 600;
  flex: 1;
}
</style>
