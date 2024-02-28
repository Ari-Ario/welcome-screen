<script setup>
// import { defineProps } from 'vue';
const welcome= '28.02.2024';
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
  font-size: 2rem;
  color: antiquewhite;
    margin-top: 2vh;
  /* border: 1px solid white; */
  border-radius: 2vw;
}
</style>