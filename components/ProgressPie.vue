<template>
  <div class="progress" :style="cpu"></div>
</template>

<script>
export default {
  name: 'ProgressPie',
  props: {
    percentage: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    cpu() {
      return {
        background: `conic-gradient(${this.getColor(this.percentage)} 0 ${this.percentage}%, rgba(0, 0, 0, 0.03) 0 100%)`,
      };
    },
  },
  methods: {
    getColor(val) {
      if (val < (100 / 3)) return '#4CAF50';
      if (val > (100 / 3) && val < 50) return '#FF9800';
      return '#F44336';
    },
  },
};
</script>

<style lang="less" scoped>
.progress {
  width: 18px;
  height: 18px;
  border-radius: 50%;
  border: 1px solid var(--progress-border-color);
}
</style>
