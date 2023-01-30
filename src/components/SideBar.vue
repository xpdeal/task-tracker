<template>
  <header>
    <h1><img width="40" src="../assets/logo.png" alt="" /> Vue test</h1>
    <hr />
    <button @click="changeThemeMode" class="button">Dark Mode</button>
  </header>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SideBar",
  data() {
    return {
      themeModeIsDark: false,
    };
  },
  emits: ["toChangedTheme"],
  methods: {
    changeThemeMode() {
      this.themeModeIsDark = !this.themeModeIsDark;
      this.$emit("toChangedTheme", this.themeModeIsDark);
    },
  },
});
</script>
<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>