<template>
  <div class="search-input">
    <div class="search-input__icon search-input__icon--left">
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-search">
        <circle cx="11" cy="11" r="8"></circle>
        <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
      </svg>
    </div>
    <input type="text" class="search-input__field" v-bind="$attrs" :value="value" @keyup="keyUp" @input="$emit('input', $event.target.value)">
    <div class="search-input__icon search-input__icon--right" :class="{'search-input__icon--show': value.length > 0}" @click="clear">
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-x">
        <line x1="18" y1="6" x2="6" y2="18"></line>
        <line x1="6" y1="6" x2="18" y2="18"></line>
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      default: '',
    },
  },
  methods: {
    clear() {
      this.$emit('input', '');
    },
    keyUp(event) {
      if (event.code === 'Escape' || event.key === 'Escape' || event.keyCode === 27) {
        this.clear();
      }
    },
  },
};
</script>

<style lang="less" scoped>
.search-input {
  position: relative;
  border-radius: 2px;
  border: 1px solid var(--filter-input--border-color);
  background: var(--filter-input--background);
  color: var(--text-color);
  -webkit-transition: all 0.3s ease;
  transition: all 0.3s ease;
  outline: none;
  width: 300px;

  &:hover {
    border-color: var(--filter-input--border-color--hover);
  }

  &:focus-within {
    border-color: var(--filter-input--border-color--focus);
  }
}

.search-input__field {
  outline: none;
  font-size: 14px;
  font-family: Montserrat, sans-serif;
  color: var(--text-color);
  padding: 8px 28px 8px 32px;
  border: none;
  width: 100%;
  background: transparent;
  font-weight: 500;
}

.search-input__icon {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}

.search-input__icon--left {
  left: 8px;
}

.search-input__icon--right {
  right: 8px;
  cursor: pointer;
  opacity: 0;
  transition: all ease 0.3s;
  visibility: hidden;
}

.search-input__icon--show {
  opacity: 1;
  visibility: visible;
}

.feather {
  display: flex;
  height: 17px;
  width: auto;
}
</style>
