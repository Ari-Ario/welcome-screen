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
  color: antiquewhite;
  border: 1px solid antiquewhite;
  border-radius: 2vw;
}

@media (max-width: 784px) {
    #welcome-cont {
    font-size: 1.5rem;
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

<!-- https://sheets.googleapis.com/v4/spreadsheets/1IAGOE_1tRhcRyWzO9em6nURZVM5acZwKJlAR7i-EPB8/values:batchGet?ranges=A2%3AE100&valueRenderOption=FORMATTED_VALUE&key=AIzaSyAjqWVpPTytrIE1ZRqtrbUOht2chryeDCk -->