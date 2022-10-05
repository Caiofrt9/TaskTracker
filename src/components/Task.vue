<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">
        {{task.description}}
      </div>
      <div class="column">
        <Cronometro :timeInSeconds='task.durationInSeconds'/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import ITask from '@/Interfaces/ITask';
import { defineComponent, PropType } from 'vue';
import Cronometro from './Cronometro.vue';

export default defineComponent({
  name: 'TaskComponent',
  components: {
    Cronometro
  },
  props: {
    task: {
      type: Object as PropType<ITask>,
      required: true,
    }
  }
})

</script>

<style scoped>
  .box {
    background: rgb(2, 175, 205);
  }
</style>
