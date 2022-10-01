<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="">
    </h1>
  </header>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';

  export default defineComponent({
    name: 'SideBar'
  })
</script>

<style scoped>
  header{
    background: #0d3b66;
    padding: 1rem;
    width: 16rem;
    height: 100vh;
  }
  @media only screen and (max-width: 768px){
    header{
      padding: 2.5rem;
      height: auto;
      width: 100%;
    }
  }
</style>