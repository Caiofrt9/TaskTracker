<template>
  <div class='box has-text-weight-bold'>
    <slot></slot>
  </div>
</template>

<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: 'BoxComponent'
})
</script>

<style scoped>
  .box {
    background: rgb(2, 175, 205);
  }
</style>
