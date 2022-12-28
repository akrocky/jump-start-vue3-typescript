<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>

    <job-list :jobs="jobs" :order="order"> </job-list>
  </div>
</template>

<script lang="ts">
let age: string | number = "25";
import { defineComponent, ref } from "vue";
import JobList from "./components/JobList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";
export default defineComponent({
  name: "App",
  components: { JobList },
  setup(props) {
    // const state = reactive({
    //   name: "Link",
    //   age: 25 as string | number,
    // });
    // return {
    //   ...toRefs(state),
    // };
    // const name = ref("Link");
    // const age = ref<number | string>(25);
    // return { name, age };
    const jobs = ref<Job[]>([
      {
        title: "farm worker",
        location: "lon lon ranch",
        salary: 30000,
        id: "1",
      },
      {
        title: "quarryman",
        location: "death mountain",
        salary: 40000,
        id: "2",
      },
      {
        title: "flute player",
        location: "the lost woods",
        salary: 35000,
        id: "3",
      },
      { title: "fisherman", location: "lake hylia", salary: 21000, id: "4" },
      {
        title: "prison guard",
        location: "gerudo valley",
        salary: 32000,
        id: "5",
      },
    ]);

    const order = ref<OrderTerm>("title");
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };
    return {
      jobs,
      order,
      handleClick,
    };
  },

  //#endregion
  methods: {},
});
</script>

<style></style>
