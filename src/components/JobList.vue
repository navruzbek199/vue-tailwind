<template>
    <div class="job_list">
        <p class=" text-md font-semibold mb-2">Ordered by {{ order }}</p>
        <transition-group name="list" tag="ul" class=" w-[1000px]">
            <li v-for="job in ordersJobs" :key="job.id" class=" bg-white px-4 py-5 w-full h-40 mb-4 rounded-md">
                <h2 class=" text-xl font-bold mb-4">{{ job.title }} in {{ job.location }}</h2>
                <p class=" text-md font-semibold text-green-500 mb-4">{{ job.salary }} dollors</p>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam enim modi dicta iusto, a molestiae magnam recusandae incidunt tempore quisquam ad. Facere provident voluptate adipisci id veniam commodi dolores obcaecati.</p>
            </li>
        </transition-group>
    </div>
</template>

<script lang="ts">
import { computed, defineComponent, type PropType } from 'vue'
import type { Job } from '@/types/Job'
import type { OrderTerm } from '@/types/OrderTerm';
export default defineComponent({
    props: {
        jobs: {
            type: Array as PropType<Job[]>,
            required: true
        },
        order: {
            type: String as PropType<OrderTerm>,
            required: true
        },
    },
    setup(props) {
        const ordersJobs = computed(() => {
            return [...props.jobs].sort((a: Job, b: Job) => {
                return a[props.order] > b[props.order] ? 1 : -1
            })
        })
        return { ordersJobs }
    },
})
</script>

<style scoped>
.list-move{
    transition: all 1s;
}
</style>