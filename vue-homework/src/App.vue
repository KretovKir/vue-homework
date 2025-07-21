<script setup>
  import { ref } from 'vue';
  import Button from './components/Button.vue'
  import Card from './components/Card.vue';
  import Header from './components/Header.vue';



  let score = ref(100)

  let cards = ref([
    {
      cardNum: '01',
      state: 'closed',
      word: 'dog',
      translation: 'Собака',
      status: 'pending'
    },
    {
      cardNum: '02',
      state: 'closed',
      word: 'camel',
      translation: 'Верблюд',
      status: 'pending'
    }

  ])
    
  

  function rotated(cardIndex, rotateStatus){
    if(rotateStatus='closed'){
///////////////ERROR!!!

      cards.value[cardIndex].state = rotateStatus
    }
   
  }

  function error(status){
    console.log(status)
    cards.value[cardIndex].status = status
  }
  function good(status){
    console.log(status)
    cards.value[cardIndex].status = status
  }


  
</script>

<template>
  <Header v-bind:score="score"/>
  <div class="cards">
    <Card v-bind='cards[0]' @statusSendError="error" @statusSendGood="good" @rotateCard="rotated" id="0"/>
    <Card v-bind='cards[1]' @statusSendError="error" @statusSendGood="good" @rotateCard="rotated" id="1"/>
  </div>
  


  <Button>
    Начать игру
  </Button>
</template>

<style scoped>
  .cards{
    display: flex;

  }
</style>
