<template>
  <tr>
    <td class="column--name">{{ workload.name }}</td>
    <td class="column--kind">{{ workload.kind }}</td>
    <td>{{ workload.namespace }}</td>
    <td>{{ workload.pods }}</td>
    <td>
      <progress-pie :percentage="workload.cpuUsage"></progress-pie>
    </td>
    <td>
      <progress-pie :percentage="workload.memoryUsage"></progress-pie>
    </td>
    <td>
      <svg v-if="workload.status === 2" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#F44336" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-alert-circle status-icon">
        <circle cx="12" cy="12" r="10"></circle>
        <line x1="12" y1="8" x2="12" y2="12"></line>
        <line x1="12" y1="16" x2="12.01" y2="16"></line>
      </svg>
      <svg v-else-if="workload.status === 1" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#FF9800" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-loader status-icon">
        <line x1="12" y1="2" x2="12" y2="6"></line>
        <line x1="12" y1="18" x2="12" y2="22"></line>
        <line x1="4.93" y1="4.93" x2="7.76" y2="7.76"></line>
        <line x1="16.24" y1="16.24" x2="19.07" y2="19.07"></line>
        <line x1="2" y1="12" x2="6" y2="12"></line>
        <line x1="18" y1="12" x2="22" y2="12"></line>
        <line x1="4.93" y1="19.07" x2="7.76" y2="16.24"></line>
        <line x1="16.24" y1="7.76" x2="19.07" y2="4.93"></line>
      </svg>
      <svg v-else xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#4CAF50" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-check status-icon">
        <polyline points="20 6 9 17 4 12"></polyline>
      </svg>
      <span>
        {{ status }}
      </span>
    </td>
    <td class="column--action">
      <button class="button button--action">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-more-horizontal button--action__icon">
          <circle cx="12" cy="12" r="1"></circle>
          <circle cx="19" cy="12" r="1"></circle>
          <circle cx="5" cy="12" r="1"></circle>
        </svg>
      </button>
    </td>
  </tr>
</template>

<script>
export default {
  name: 'WorkloadListItem',
  props: {
    workload: {
      type: Object,
      default: () => { },
    },
  },
  computed: {
    status() {
      if (this.workload.status === 0) return 'Running';
      if (this.workload.status === 2) return 'CrashLoopBackOff';
      return 'Init';
    },
    cpu() {
      return {
        background: `conic-gradient(${this.percentage(this.workload.cpuUsage)} 0 ${this.workload.cpuUsage}%, rgba(0, 0, 0, 0.03) 0 100%)`,
      };
    },
  },
  methods: {
    percentage(val) {
      if (val < (100 / 3)) return '#4CAF50';
      if (val > (100 / 3) && val < 50) return '#FF9800';
      return '#F44336';
    },
  },
};
</script>

<style lang="less" scoped>
td {
  padding: 15px 10px;
  border-bottom: 1px solid var(--sidebar-border-color);
  vertical-align: middle;
}

.status-icon {
  display: inline-block;
  height: 18px;
  width: auto;
  vertical-align: sub;
  margin-right: 5px;
}
tr {
  transition: all ease 0.3s;
  cursor: pointer;
}
tr:hover {
  background-color: var(--workload-item-background);
}
</style>
