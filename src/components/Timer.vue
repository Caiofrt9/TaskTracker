<template>

  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :timeInSeconds='timeInSeconds' />
    <button class="button" @click="handleStart" :disabled="timeIsCounting">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>

    <button class="button" @click="handleStop" :disabled="!timeIsCounting">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>

</template>

<script lang="ts">
  import { defineComponent } from "vue";
  import Cronometro from "./Cronometro.vue";
  
  export default defineComponent({
      name: "handleComponent",
      emits: ["aoTemporizadorFinalizado"],
      components: {
        Cronometro
      },
      data() {
          return {
              timeInSeconds: 0,
              cronometro: 0,
              timeIsCounting: false,
          };
      },
      methods: {
          handleStart() {
              this.timeIsCounting = true
              this.cronometro = setInterval(() => {
                  this.timeInSeconds += 1;
              }, 1000);
          },
          handleStop() {
            this.timeIsCounting = false
              clearInterval(this.cronometro);
              this.$emit('aoTemporizadorFinalizado', this.timeInSeconds)
              this.timeInSeconds = 0 
          },
      },
  });
  </script>
  