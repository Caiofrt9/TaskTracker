<template>
  <Box>
    <div class="columns">
      <div class="column is-7">
        {{task.description || 'Tarefa sem descrição'}}
      </div>
      <div class="column">
        <Cronometro :timeInSeconds='task.durationInSeconds'/>
      </div>
    </div>
  </Box>
</template>

<script lang="ts">
import ITask from '@/Interfaces/ITask';
import { defineComponent, PropType } from 'vue';
import Cronometro from './Cronometro.vue';
import Box from './Box.vue';

export default defineComponent({
  name: 'TaskComponent',
  components: {
    Cronometro,
    Box
},
  props: {
    task: {
      type: Object as PropType<ITask>,
      required: true,
    }
  }
})

</script>

