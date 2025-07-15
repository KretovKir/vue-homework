<script setup>
import Score from './Score.vue';


</script>

<template>
  <div class="header">  
    <h3>Запомни слово</h3>
    <Score score="100"/>
  </div>
</template>

<style scoped>
  .header{
    display: flex;
    justify-content: space-between;
  }
</style>