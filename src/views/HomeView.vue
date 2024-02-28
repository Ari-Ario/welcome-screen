<script setup>
import TheWelcome from '../components/TheWelcome.vue'
import { RouterLink, RouterView } from 'vue-router'
import card from '../components/screenCompos/mainCard.vue'

</script>

<template>
  <!-- <nav>
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/about">About</RouterLink>
  </nav> -->
  <main>
    <card />
  </main>
</template>

<style scoped>
main {
  display: block;
  top: 0;
  text-align: center;
  width: 94vw;

}
</style>