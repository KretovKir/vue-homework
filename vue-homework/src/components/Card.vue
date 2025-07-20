<script setup>
import { ref } from 'vue';
import Error from './Error.vue';
import Good from './Good.vue';

  const emit = defineEmits(['rotateCard', 'statusSendError', 'statusSendGood'])
  const props = defineProps(['cardNum', 'word', 'translation'])
  
  
  
  
  function rotation(event){
    const parent = event.target.closest('.card')
    parent.classList.toggle('flipped')
    emit('rotateCard', 'open')
  }

  function statusSendError(){
    emit('statusSendError', 'fail')
  }

  function statusSendGood(){
    emit('statusSendGood', 'success')
  }

 

  

  
</script>

<template>
  <div class="card-container">
    <div class="card" @click="rotation">

        <div class="front">
          <div class="card-border">
            <span class="card-num">{{ props.cardNum }}</span>
            <span class="word">{{ props.word }}</span>
          </div>
        </div>

        <div class="back">
          <div class="card-border">
            <span class="word">{{ props.translation }}</span>
          </div>
          
          <div class="card-controllers">
            <Error @click="statusSendError"></Error>
            <Good @click="statusSendGood"></Good>
        </div>
        </div>
        
    </div>
  </div>
</template>

<style scoped>
  
  .card {
  width: 250px;
  height: 376px;
  padding: 24px;
  border-radius: 36px;
  box-shadow: 0px 0px 16px rgba(0,0,0,0.1);
  position: relative;
  transform-style: preserve-3d;
  transition: transform 0.8s;
}


.card.flipped {
  transform: rotateY(180deg);
  position: relative;
}


.front, .back {
  position: absolute;
  min-width: 100%;
  min-height: 100%;
  backface-visibility: hidden; 
  display: flex;
  align-items: center;
  justify-content: center;
}


/* Обратная сторона */
.back {
  background-color: #fff;
  transform: rotateY(180deg);
}

.card-border{
    border:1px solid rgba(204,232,255,1);
    border-radius:12px;
    width: 100%;
    height: 100%;
    display:flex;
    justify-content:center;
    align-items:center;
}
.card-num{
    position:absolute;
    left:20px;
    top:-10px;
    color:#000;
    background-color:#fff; /* пример цвета */
}
.card-controllers{
    position:absolute;
    bottom:0;
    left:50%;
    transform:translateX(-50%);
}
</style>