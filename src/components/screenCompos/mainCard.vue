<script setup>
import {onBeforeMount, onMounted, ref} from 'vue';
import welcome from './welcome.vue'
import day from './theDay.vue'
import info from './infoBlock.vue'

const dataUrl = ref("")
const date = ref("")
const name = ref("")
const description = ref("")

async function fetchData() {
  const res = await fetch('https://randomuser.me/api/');
  const data = await res.json();
  name.value = data.results[0].name.first;
  date.value = data.results[0].name.first;
  description.value = data.results[0].name.last;
  dataUrl.value = data.results[0].email;
}
const allData= fetchData() 
</script>

<template>
  <div class="user-container">
    <welcome />
    <day />
      <div class="info-container">
        <info :info="name" />
        <info :info="description" />
        <info class="user-email" :info="dataUrl" />
        <button class="card-button" @click="fetchData()">Next day</button>
      </div>
    </div>
</template>

<style scoped>
.user-container {
  display: block;
  top: 0;
  text-align: center;

}
.card-button {
    font-size: 3rem;
    color: rgb(15, 15, 15);
    background-color: antiquewhite;
    margin-top: 2vh;
    border-radius: 2vw;
}
</style>