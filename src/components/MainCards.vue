<script setup>
  import MainCardsSingle from './MainCardsSingle.vue'
</script>

<template>
  <div class="subwrapper">
    <MainCardsSingle v-for="n in 20"/>
  </div>
</template>

<style scoped lang="postcss">
  .subwrapper {
    @apply grid-cols-1 gap-4 md:grid lg:grid-cols-3 xl:grid-cols-4;
  }
</style>
