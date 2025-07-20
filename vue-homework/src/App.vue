<script setup>
  import { ref } from 'vue';
import Button from './components/Button.vue'
  import Card from './components/Card.vue';
  import Header from './components/Header.vue';

  let cardData = ref({
    cardNum: '01',
    state: 'closed',
    word: 'dog',
    translation: 'Собака',
    status: 'pending'
  })

  function rotated(rotateStatus){
    cardData.value.state = rotateStatus
  }

  function error(status){
    console.log(status)
    cardData.value.status = status
  }
  function good(status){
    console.log(status)
    cardData.value.status = status
  }


  
</script>

<template>
  <Header/>

  <Card v-bind='cardData' @statusSendError="error" @statusSendGood="good" @rotateCard="rotated"/>


  <Button>
    Начать игру
  </Button>
</template>

<style scoped>

</style>
