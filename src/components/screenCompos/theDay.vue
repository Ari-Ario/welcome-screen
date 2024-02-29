<script setup>
// import { defineProps } from 'vue';
import { defineProps } from 'vue';
const props = defineProps({
  day: String,
}
  );

// AIzaSyCQsMBv9KSBUdC7775MULa8oXjLFbfpPOQ
</script>
<template>
      <div v-if="day" id="day-cont">{{ day }} </div>
</template>

<style scoped>
span {
    font-size: 4rem;
    color: white;
}

#day-cont {
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