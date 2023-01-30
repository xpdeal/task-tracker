<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <BoxForm />
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue';
import BoxForm from './components/BoxForm.vue';

export default defineComponent({
  name: 'App',
  components:{
    SideBar,
    BoxForm
  }
 
});
</script>

<style>

</style>
