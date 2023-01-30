<template>
  <BoxOne>
    <div class="columns">
      <div class="column is-7">{{ task.taskName || "Sem descrição" }}</div>
      <div class="columun">{{ task.taskCountdown }}</div>
    </div>
  </BoxOne>
</template>
<script lang="ts">
import TaskInterface from "@/interfaces/TaskInterface";
import { defineComponent, PropType } from "vue";
import BoxOne from "./BoxOne.vue";
export default defineComponent({
  name: "TaskList",
  components: {
    BoxOne,
  },
  props: {
    task: {
      type: Object as PropType<TaskInterface>,
      required: true,
    },
  },
});
</script>
