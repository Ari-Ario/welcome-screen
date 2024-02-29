<script setup>
import { defineProps } from 'vue';
const props = defineProps({
  info: String,
  descritpion: String,
  address: String
}
  );
</script>
<template>
  <div>
    <h2>{{ title }}</h2>
    <p>{{  descritpion }}</p>
  </div>
    <div v-if="info" class="info-container" :info="info" :description="descritpion" :address="address">{{ info }} {{ descritpion }} {{ address }}</div>
</template>

<style scoped>
.info-container {
    display: block;
    font-size: 3rem;
    color: rgb(15, 15, 15);
    background-color: antiquewhite;
    margin-top: 2vh;
    border-radius: 2vw;
}

@media (max-width: 784px) {
    .info-container {
    font-size: 1.5rem;
}
}
</style>