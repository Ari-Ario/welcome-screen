<script setup>
// import { defineProps } from 'vue';
const welcome= 'Welcome to opportunity';
</script>
<template>
    <div id="welcome-cont">{{ welcome }}</div>
</template>

<style scoped>
span {
    font-size: 4rem;
    color: white;
}

#welcome-cont {
  display: block;
  top: 0;
  text-align: center;
  font-size: 3rem;
  color: white;
  width: 100%;
  border: 1px solid white;
  border-radius: 2vw;
}
</style>