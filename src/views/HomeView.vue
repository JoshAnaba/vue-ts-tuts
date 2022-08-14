<template>
  <div class="home">
    <!-- <div> -->
    <div class="order-by">
      <p>Order by</p>
      <button @click="handleClick('salary')">Salary</button>
      <button @click="handleClick('title')">Title</button>
      <button @click="handleClick('location')">Location</button>
    </div>
    <JobsList :jobs="jobs" :order="order" />
    <!-- </div> -->
  </div>
</template>

<script lang="ts">
// eslint-disable-next-line @typescript-eslint/no-unused-vars
import { defineComponent, reactive, toRefs, ref } from "vue";
import JobsList from "@/components/JobsList.vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";
export default defineComponent({
  name: "HomeView",
  components: {
    JobsList,
  },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "Farm worker",
        location: "Lon lon ranch",
        salary: 30000,
        id: "1",
      },
      {
        title: "Software Devr",
        location: "LDN",
        salary: 300000,
        id: "2",
      },
      {
        title: "Pastor",
        location: "Kenya",
        salary: 20000,
        id: "3",
      },
      {
        title: "Laundryman",
        location: "America",
        salary: 10000,
        id: "4",
      },
      {
        title: "Artiste",
        location: "Nigeria",
        salary: 34000,
        id: "5",
      },
      {
        title: "Bus Driver",
        location: "China",
        salary: 1000,
        id: "6",
      },
    ]);
    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }
    return {
      jobs,
      handleClick,
      order
    };
  },
});
</script>

<style scoped>
.order-by button {
  margin-right: 10px;
}
</style>
