<template>
  <div class="page">
    <div class="container">
      <header class="page__header">
        <div class="row row--center-v">
          <div class="column">
            <h1 class="page__title">
              Workloads
            </h1>
          </div>
          <div class="column column--wrap">
            <filter-input v-model="filter" placeholder="Type to filter..."></filter-input>
          </div>
        </div>
      </header>
      <section class="page__body">
        <table class="table">
          <thead>
            <tr>
              <th class="column-name">Name</th>
              <th class="column-kind">Kind</th>
              <th class="column-namespace">Namespace</th>
              <th class="column-pods">Pods</th>
              <th class="column-cpu">CPU Usage</th>
              <th class="column-memory">Mem Usage</th>
              <th class="column-status">Status</th>
              <th class="column-action"></th>
            </tr>
          </thead>
          <tbody>
            <workload-list-item v-for="workload in filteredWorkloads" :key="workload.id" :workload="workload"></workload-list-item>
          </tbody>
        </table>
      </section>
      <footer class="page__footer"></footer>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Workloads',
  data() {
    return {
      workloads: [],
      filter: '',
    };
  },
  computed: {
    filteredWorkloads() {
      if (this.filter.length === 0) return this.workloads;
      const q = this.filter.toLowerCase();
      return this.workloads.filter((x) => x.name.toLowerCase().includes(q));
    },
  },
  mounted() {
    for (let i = 0; i < 100; i += 1) {
      this.workloads.push({
        id: i,
        name: this.generateName(),
        kind: 'Pod',
        namespace: 'default',
        pods: Math.floor(Math.random() * 6) + 1,
        cpuUsage: Math.floor(Math.random() * 100) + 1,
        memoryUsage: Math.floor(Math.random() * 100) + 1,
        status: this.getStatus(),
      });
    }
  },
  methods: {
    getStatus() {
      const val = (Math.floor(Math.random() * 20) + 1);
      if (val % 2 === 0) return 1;
      if (val % 3 === 0) return 2;

      return 0;
    },
    generateName() {
      return `${this.getName()}-${this.getName()}-${this.getName()}${this.getName()}`;
    },
    getName() {
      return Math.floor((Math.random()) * 0x10000).toString(16);
    },
  },
};
</script>

<style lang="less" scoped>
.table {
  font-size: 14px;
}

th {
  font-weight: 700;
  border-bottom: 1px solid var(--th-border-color);
  text-align: left;
  padding: 15px 10px;
}

.column-action {
  width: 30px;
}

.column-cpu,
.column-memory {
  width: 150px;
}

.column-status {
  width: 200px;
}
</style>
