<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>Jobs List</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobsList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from 'vue';
import JobModel from './models/job.model';
import SortTermType from './models/sortTerm.type';
import JobsList from './components/JobsList.vue';

export default defineComponent({
  name: 'App',
  components: { JobsList },

  setup() {
    const jobs = ref<JobModel[]>([
      {
        title: 'farm worker',
        location: 'Italy',
        salary: 30000,
        id: '1',
      },
      {
        title: 'truck driver',
        location: 'UK',
        salary: 40000,
        id: '2',
      },
      {
        title: 'manager',
        location: 'Germany',
        salary: 35000,
        id: '3',
      },
      {
        title: 'dance instructor',
        location: 'Macedonia',
        salary: 21000,
        id: '4',
      },
      {
        title: 'prison guard',
        location: 'Austria',
        salary: 32000,
        id: '5',
      },
    ]);

    const order = ref<SortTermType>('title');

    const handleClick = (term: SortTermType) => {
      order.value = term;
    };

    return {
      jobs,
      handleClick,
      order,
    };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
