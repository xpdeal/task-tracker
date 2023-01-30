<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
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
  },
});
</script>

<style scoped>
.taskList {
  padding: 10px;
}
</style>
