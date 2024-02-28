<script setup>
import home from './views/HomeView.vue'

</script>

<template>
  <div class="main">
    <home />
  </div>
</template>

<style scoped>
.main {
  display: block;
  top: 0;
  text-align: center;
  width: 100%;
}

@media (min-width: 784px) {
  .main {
  width: 100%;
}
  .logo {
    margin: 0 2rem 0 0;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
