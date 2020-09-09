<template>
  <aside class="sidebar">
    <header class="sidebar__header"></header>
    <section class="sidebar__body">
      <div class="sidebar__title">
        <div class="sidebar__title__label">
          Namespaces
        </div>
      </div>
      <menu-item v-for="item in namespaces" :key="item" :title="item"></menu-item>
    </section>
    <footer class="sidebar__footer" @click="toggleDarkTheme">
      <div class="row row--center-v">
        <div class="column column--wrap">
          <svg v-if="useDarkTheme" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-toggle-left">
            <rect x="1" y="5" width="22" height="14" rx="7" ry="7"></rect>
            <circle cx="8" cy="12" r="3"></circle>
          </svg>
          <svg v-else xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-toggle-right">
            <rect x="1" y="5" width="22" height="14" rx="7" ry="7"></rect>
            <circle cx="16" cy="12" r="3"></circle>
          </svg>
        </div>
        <div class="column">
          <span>Dark theme</span>
        </div>
      </div>

    </footer>
  </aside>
</template>

<script>
export default {
  name: 'SideBar',
  data() {
    return {
      useDarkTheme: false,
      namespaces: [],
    };
  },
  watch: {
    useDarkTheme(newVal) {
      if (!newVal) {
        document.body.classList.remove('dark--theme');
      } else {
        document.body.classList.add('dark--theme');
      }
    },
  },
  mounted() {
    for (let i = 0; i < 100; i += 1) {
      this.namespaces.push(`Cluster #${i}`);
    }
  },
  methods: {
    toggleDarkTheme() {
      this.useDarkTheme = !document.body.classList.contains('dark--theme');
    },
  },
};
</script>

<style lang="less" scoped>
.sidebar {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  width: 300px;
  background: var(--sidebar-background-color);
  border-right: 1px solid var(--sidebar-border-color);
  display: flex;
  flex-direction: column;
}

.sidebar__body {
  flex: 1;
  padding: 5px 15px;
  overflow-y: auto;
}

.sidebar__title {
  display: flex;
  margin-bottom: 5px;
  margin-top: 10px;
  opacity: 0.75;
}

.sidebar__title__label {
  font-size: 14px;
  font-weight: 500;
  flex: 1;
}

.sidebar__footer {
  padding: 5px;
  font-size: 14px;
  transition: all ease 0.3s;
  cursor: pointer;

  &:hover {
    background: var(--menu-item-background);
  }
}

.feather {
  display: inline-block;
}
</style>
