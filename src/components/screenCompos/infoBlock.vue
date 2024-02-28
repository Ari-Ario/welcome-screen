<script setup>
import { defineProps } from 'vue';
const props = defineProps({
  info: String,
}
  );
</script>
<template>
    <div v-if="info" class="info-container">{{ info }}</div>
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