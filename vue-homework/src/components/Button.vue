<script setup>
</script>

<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<style scoped>
  .btn{
    width: 335px;
    height: 68px;
    padding: 10px 16px;
    border-radius: 100px;
    font-family: 'Roboto';
    font-weight: 400;
    font-size: 24px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #008BFE;
    color: #fff;
    border: none;
  }
</style>