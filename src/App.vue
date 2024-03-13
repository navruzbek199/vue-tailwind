<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from 'vue';
import JobList from './components/JobList.vue';
// import { OrderTerm } from '@types/OrderTerm';
export type OrderTerm = 'location' | 'title' | 'salary'
export default defineComponent({
  name: 'App',
  components: {
    JobList
  },
  setup(){

    const jobs = ref([
      {title: 'Vue Developer', location: 'Tashkent, Uzbekistan', salary: 3000, id: 1},
      {title: 'React Developer', location: 'Samarqand, Uzbekistan', salary: 2100, id: 2},
      {title: 'Angular Developer', location: 'Jizzakh, Uzbekistan', salary: 2500, id: 3},
      {title: 'Go Developer', location: 'Navoi, Uzbekistan', salary: 3500, id: 4},
      {title: 'Node Developer', location: 'Qarshi, Uzbekistan', salary: 2700, id: 5},
      {title: 'Php Developer', location: 'Andijan, Uzbekistan', salary: 1750, id: 6},
    ])

    const order = ref<OrderTerm>('salary')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order }
  },
})

</script>

<template>
  <div class="app mx-auto justify-center grid py-9 h-full bg-slate-200">
    <header class=" flex items-center justify-center gap-4">
      <button @click="handleClick('title')" class="border border-indigo-700 px-4 py-2 rounded-lg text-indigo-600">Order by title</button>
      <button @click="handleClick('location')" class="border border-indigo-700 px-4 py-2 rounded-lg text-indigo-600">Order by location</button>
      <button @click="handleClick('salary')" class="border border-indigo-700 px-4 py-2 rounded-lg text-indigo-600">Order by salary</button>
    </header>
    <JobList :jobs="jobs" :order="order"/>
  </div>
</template>

<style scoped>
  
</style>
