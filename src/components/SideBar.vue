<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="">
    </h1>
    <button class="button" @click="darkMode">
      {{textButton}}
    </button>
  </header>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';

  export default defineComponent({
    name: 'SideBar',
    emits: ['aoTemaAlterado'],
    data () {
      return {
        darkModeActive: false
      }
    },
    computed: {
      textButton () {
        if (this.darkModeActive) {
          return 'LightMode'
        }
        return "DarkMode"
      }
    },
    methods: {
      darkMode () { 
        this.darkModeActive = !this.darkModeActive
        this.$emit('aoTemaAlterado', this.darkModeActive)
      }
    },
  })
</script>

<style scoped>
  header{
    background: #0d3b66;
    padding: 1rem;
    width: 100%;
    height: 100vh;
    text-align: center;
  }
  
  @media only screen and (max-width: 768px){
    header{
      padding: 2.5rem;
      height: auto;
    }
  }
</style>