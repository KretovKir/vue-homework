<script setup>
import { ref } from 'vue';
import Score from './Score.vue';

let props = defineProps(['score'])

</script>

<template>
  <div class="header">  
    <h3>Запомни слово</h3>
    <Score :score = 'props.score'>
      {{ props.score }}
    </Score>

  </div>
</template>

<style scoped>
  .header{
    display: flex;
    justify-content: space-between;
  }
</style>