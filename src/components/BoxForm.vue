<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário de criação de nova tarefa"
      >
        <input type="text" class="input" placeholder="Nome da tarefa" />
      </div>
      <div class="column">
        <div
          class="is-flex is-align-items-center is-justify-content-space-between"
        >
          <section>
            <strong>{{ timeRunning }}</strong>
          </section>
          <button @click="start" class="button">
            <span class="icon">
              <i class="fas fa-play"></i>
            </span>
            <span>play</span>
          </button>
          <button @click="stop" class="button">
            <span class="icon">
              <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "BoxForm",
  data() {
    return {
      timeInSeconds: 0,
    };
  },
  computed: {
    timeRunning(): string {
      return new Date(this.timeInSeconds * 1000).toISOString().substr(11, 8);
    },
  },
  methods: {
    start() {
      setInterval(() => {
        console.log("contando...");
        this.timeInSeconds += 1;
      }, 1000);
      console.log("started...");
    },
    stop() {
      console.log("stopped...");
    },
  },
});
</script>
<style scoped>
</style>