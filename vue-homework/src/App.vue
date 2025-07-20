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

  

  function rotated(rotateStatus){
    cards.value.state = rotateStatus
  }

  function error(status){
    console.log(status)
    cards.value.status = status
  }
  function good(status){
    console.log(status)
    cards.value.status = status
  }


  
</script>

<template>
  <Header v-bind:score="score"/>

  <Card v-bind='cards[0]' @statusSendError="error" @statusSendGood="good" @rotateCard="rotated"/>
  <Card v-bind='cards[1]' @statusSendError="error" @statusSendGood="good" @rotateCard="rotated"/>


  <Button>
    Начать игру
  </Button>
</template>

<style scoped>

</style>
