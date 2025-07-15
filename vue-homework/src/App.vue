<script setup>
  import Button from './components/Button.vue'
  import Card from './components/Card.vue';
  import Header from './components/Header.vue';


  function error(status){
    console.log(status)
  }
  function good(status){
    console.log(status)
  }
</script>

<template>
  <Header/>

  <Card cardNum="01" word="dog" translatedWord="собака" @statusSendError="error" @statusSendGood="good"/>


  <Button>
    Начать игру
  </Button>
</template>

<style scoped>

</style>
