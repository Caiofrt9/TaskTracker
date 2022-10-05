<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar/>
    </div>

    <div class="column is-three-quarter">
      <TaskForm @aoSalvarTarefa="saveTask"/>
      <div class="list">
        <Task v-for='(task , index) in tasks' :key='index' :task="task"/>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue';
import TaskForm from './components/TaskForm.vue';
import Task from './components/Task.vue';
import ITask from './Interfaces/ITask';

export default defineComponent({
    name: "App",
    components: { SideBar, TaskForm, Task},
    data () {
      return {
        tasks: [] as ITask[]
      }
    },
    methods: {
      saveTask (task: ITask) {
        this.tasks.push(task)
      }
    }
});
</script>

<style>
  .list {
    padding: 1.5rem
  }
</style>
