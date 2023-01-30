<template>
  <div class="box has-text-weigth-bold">
    <slot></slot>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BoxOne",
});
</script>
<style scoped>
.box {
  background-color: antiquewhite;
}
</style>