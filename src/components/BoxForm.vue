<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário de criação de nova tarefa"
      >
        <input
          type="text"
          v-model="taskName"
          class="input"
          placeholder="Nome da tarefa"
        />
      </div>
      <div class="column">
        <TimerBar @toStopCountDown="closeTask" />
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import TimerBar from "./TimerBar.vue";
export default defineComponent({
  name: "BoxForm",
  components: {
    TimerBar,
  },
  emits: ["toTaskSave"],
  methods: {
    closeTask(totalTime: number): void {
      this.$emit("toTaskSave", {
        taskCountdown: totalTime,
        taskName: this.taskName,
      });
      this.taskName = "";
    },
  },
  data() {
    return {
      taskName: "",
    };
  },
});
</script>
<style scoped>
</style>