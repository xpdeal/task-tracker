<template>
  <main
    class="columns is-gapless is-multiline"
    :class="{ 'dark-mode': darkModeTheme }"
  >
    <div class="column is-one-quarter">
      <SideBar @toChangedTheme="changeThemeMode" />
    </div>
    <div class="column is-three-quarter content-app">
      <BoxForm @toTaskSave="taskSave" />
      <div class="taskList">
        <TaskList v-for="(task, index) in tasks" :key="index" :task="task" />
        <BoxOne v-if="taskListIsEmpty">
          <hr />
          Você ainda não tem atividades hoje
        </BoxOne>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBar from "./components/SideBar.vue";
import BoxForm from "./components/BoxForm.vue";
import TaskList from "./components/TaskList.vue";
import TaskInterface from "./interfaces/TaskInterface";
export default defineComponent({
  name: "App",
  components: {
    SideBar,
    BoxForm,
    TaskList,
  },
  data() {
    return {
      tasks: [] as TaskInterface[],
      darkModeTheme: false,
    };
  },
  computed: {
    taskListIsEmpty(): boolean {
      return this.tasks.length === 0;
    },
  },
  methods: {
    taskSave(task: TaskInterface) {
      this.tasks.push(task);
    },
    changeThemeMode(darkMode: boolean) {
      console.log("mode ");
      this.darkModeTheme = darkMode;
    },
  },
});
</script>

<style scoped>
main {
  --bg-primary: #fff;
  --text-primary: #000;
}
main.dark-mode {
  --bg-primary: #000;
  --text-primary: #fff;
}
.taskList {
  padding: 10px;
}
.content-app {
  background-color: var(--bg-primary);
  color: var(--text-primary);
}
</style>
