<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
        <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="description" />
      </div>
      <div class="column">
        <Timer @aoTemporizadorFinalizado='finishTask' />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Timer from "./Timer.vue";

export default defineComponent({
  name: "TaskForm",
  emits: ['aoSalvarTarefa'],
  components: {
    Timer
  },
  data() {
    return {
      description: ''
    }
  },
  methods: {
    finishTask(elapsedTime: number): void {
      this.$emit('aoSalvarTarefa', {
        durationInSeconds: elapsedTime,
        description: this.description
      })
      this.description = ''
    }
  }
});
</script>
