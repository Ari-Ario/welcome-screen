<script setup>
import { defineProps } from 'vue';
const props = defineProps({
  time: String,
  descritpion: String,
  address: String
}
  );
</script>
<template>
    <div v-if="time" class="info-container" :time="time" :description="descritpion" :address="address">
    <h5 class="info">{{ time }}</h5> 
    <h5 class="desc">{{ descritpion }}</h5> 
    <h6 class="addr">{{ address }}</h6>
    </div>
</template>

<style scoped>
.info-container {
    display: flex;
    flex-direction: column; 
    justify-content: flex-start;
    align-items: flex-start;
    font-size: 2rem;
    color: rgb(15, 15, 15);
    background-color: antiquewhite;
    margin-top: 2vh;
    padding-left: 4vw;
    border-radius: 2vw;
}
.info {
  color: rgb(87, 3, 3);
}
.desc {
  color: rgb(0, 36, 0);
}
.addr {
  color: rgb(0, 0, 74);
}

@media (max-width: 784px) {
    .info-container {
    font-size: 1.5rem;
}
}
</style>