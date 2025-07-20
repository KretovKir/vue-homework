<script setup>
  import { ref } from "vue";
import IconHeart from "./IconHeart.vue";
  

 let props = defineProps(['score'])

  
</script>

<template>
  <div class="score-container">
    <span class="score-count">{{ props.score }}</span>
    <IconHeart></IconHeart>
  </div>

  
</template>

<style scoped>
  .score-container{
    width: 110px;
    padding: 12px 24px;
    border-radius: 36px;
    background-color: #CCE8FF;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .score-count{
    font-family: 'Roboto';
    font-weight: 700;
    font-size: 16px;
    line-height: 24px;
    letter-spacing: 0%;
    text-align: center;
    margin-right: 12px;
    color: #008BFE;
  }
</style>