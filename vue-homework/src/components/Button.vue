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
    font-family: var(--font);
    font-weight: 400;
    font-size: 24px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: var(--color-btn-bg);
    color: var(--color-primary);
    border: none;
  }
</style>