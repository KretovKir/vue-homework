<script setup>
  const now = new Date();
  const year = now.getFullYear();
  const month = now.getMonth() + 1
  const day = now.getDate();
  const formattedDate = `${year}-${month}-${day}`

</script>

<template>
  <h1>{{ formattedDate }}</h1>
</template>

<style scoped>

</style>
