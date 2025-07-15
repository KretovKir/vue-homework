<script setup>
import Error from './Error.vue';
import Good from './Good.vue';

  const {cardNum, word} = defineProps(['cardNum', 'word', 'translatedWord'])
  const emits = defineEmits(['rotateCard', 'statusSendError', 'statusSendGood'])

  function rotation(){
    emits('rotateCard', 'rotate')
    document.querySelector('.card').classList.add('rotating')
  }

  function statusSendError(){

    emits('statusSendError', 'error')
  }

  function statusSendGood(){
    emits('statusSendGood', 'good')
  }
</script>

<template>
  <div class="card" @click="rotation">
    <!-- <div class="front">
      <div class="card-border">
        <span class="card-num">{{ cardNum }}</span>
        <span class="word">{{ word }}</span>
      </div>
    </div> -->
    
      <div class="card-border">
        <span class="card-num">{{ cardNum }}</span>
        <span class="translatedWord">{{ translatedWord }}</span>
        <div class="controllers">
          <Error @click="statusSendError"></Error>
          <Good @click="statusSendGood"></Good>
        </div>
      </div>
    
  </div>
</template>

<style scoped>
  .card{
    width: 250px;
    height: 376px;
    padding: 24px;
    border-radius: 36px;
    box-shadow: 0px 0px 16px 0px rgba(0, 0, 0, 0.1);
    
  }

  .front, .back {
    position: absolute;
    backface-visibility: hidden; /* скрывать обратную сторону при перевороте */
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    backface-visibility: hidden; 
  }

  .front {
  background-color: #fff;
  }

  /* Обратная сторона, повернутая на 180 градусов по Y */
  .back {
    background-color: #f0f0f0;
    transform: rotateY(180deg);
  }
  .card-border{
    border: 1px solid rgba(204, 232, 255, 1);
    border-radius: 12px;
    position: relative;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .card-num{
    position: absolute;
    left: 20px;
    top: -10px;
    color: #000;
    background-color: var(--color-primary);
  }

  .controllers{
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translate(-50%, 0);
  }
</style>