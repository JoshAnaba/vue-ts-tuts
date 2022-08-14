<template>
  <section class="job-list">
    <p>Ordered by {{order}}</p>
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
      <h2>{{job.title}} in {{job.location}}</h2>
      <div class="salary">
        <p>{{job.salary}} dollars</p>
      </div>
      <div class="description">
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium nostrum perspiciatis eius illo inventore voluptates alias consequuntur provident nisi laborum, porro dolores atque animi eaque reiciendis? Nostrum officiis fugiat porro!
        </p>
      </div>
      </li>
    </ul>
  </section>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from 'vue'
import Job from '@/types/Job'
import OrderTerm from '@/types/OrderTerm'
export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>
    }
  },
  setup (props) {
    const orderedJobs = computed(()=> {
      return [...props.jobs].sort((a: Job, b: Job)=>{
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })
    return {
      orderedJobs
    }
  }
})
</script>


<style scoped>

</style>
