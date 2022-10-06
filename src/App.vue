<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro' : darkModeActive}">
    <div class="column is-one-quarter">
      <SideBar @aoTemaAlterado="changeTeme"/>
    </div>

    <div class="column is-three-quarter conteudo">
      <TaskForm @aoSalvarTarefa="saveTask"/>
      <div class="list">
        <Task v-for='(task , index) in tasks' :key='index' :task="task"/>

        <Box v-if="listIsEmpty">
          Você não está muito produtivo hoje :(
        </Box>
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
import Box from './components/Box.vue';

export default defineComponent({
    name: "App",
    components: { SideBar, TaskForm, Task, Box },
    data () {
      return {
        tasks: [] as ITask[],
        darkModeActive: false
      }
    },
    computed: {
      listIsEmpty () : boolean{
        return this.tasks.length === 0
      }
    },
    methods: {
      saveTask (task: ITask) {
        this.tasks.push(task)
      },
      changeTeme (darkModeActive: boolean) {
        this.darkModeActive = darkModeActive
      }
    }
});
</script>

<style>
  .list {
    padding: 1.25rem
  }
  main {
    --bg-primario: #fff;
    --texto-primario: #000;
  }
  main.modo-escuro {
    --bg-primario: #2b2d42;
    --texto-primario: #ddd;
  }
  .conteudo {
    background-color: var(--bg-primario);
  }
</style>
