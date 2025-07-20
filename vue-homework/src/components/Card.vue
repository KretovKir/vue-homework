<script setup>
import { ref } from 'vue';
import Error from './Error.vue';
import Good from './Good.vue';

  
  const emits = defineEmits(['rotateCard', 'statusSendError', 'statusSendGood'])
  let cardNum = ref('01')
  let state = ref('closed')
  let word = ref('Dog')
  let translation = ref('Собака')
  let status = ref('pending')
  
  function rotation(event){
    emits('rotateCard', 'rotate')
    const parent = event.target.closest('.card')
    parent.classList.toggle('flipped')
    state.value = 'opened'
    console.log(state.value)
  }

  function statusSendError(){
    status.value = 'fail'
    emits('statusSendError', 'error')
  }

  function statusSendGood(){
    status.value = 'pending'
    emits('statusSendGood', 'good')
  }

 

  

  
</script>

<template>
  <div class="card-container">
    <div class="card" @click="rotation">

        <div class="front">
          <div class="card-border">
            <span class="card-num">{{ cardNum }}</span>
            <span class="word">{{ word }}</span>
          </div>
        </div>

        <div class="back">
          <div class="card-border">
            <span class="word">{{ translation }}</span>
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