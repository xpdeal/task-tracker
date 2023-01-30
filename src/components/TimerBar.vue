<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CountDown :timeInSeconds="timeInSeconds" />
    <button @click="start" class="button" :disabled="isCounting">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button @click="stop" class="button" :disabled="!isCounting">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import CountDown from "./CountDown.vue";
export default defineComponent({
  name: "TimerBar",
  components: {
    CountDown,
  },
  data() {
    return {
      timeInSeconds: 0,
      countdown: 0,
      isCounting: false,
    };
  },
  emits: ["toStopCountDown"],
  methods: {
    start() {
      this.isCounting = true;
      this.countdown = setInterval(() => {
        console.log("contando...");
        this.timeInSeconds += 1;
      }, 1000);
      console.log("started...");
    },
    stop() {
      this.isCounting = false;
      clearInterval(this.countdown);
      this.$emit("toStopCountDown", this.timeInSeconds);
      this.timeInSeconds = 0;
    },
  },
});
</script>