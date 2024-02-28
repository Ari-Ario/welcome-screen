<script setup>
import {onBeforeMount, onMounted, ref} from 'vue';
import welcome from './welcome.vue'
import day from './theDay.vue'
import info from './infoBlock.vue'
const sheet_id = import.meta.env.VITE_GOOGLE_SHEET_ID;
const api_token = import.meta.env.VITE_GOOGLE_API_KEY;

const dataUrl = ref("")
const date = ref("")
const name = ref("")
const description = ref("")

async function fetchData() {
  const res = await fetch(`https://sheets.googleapis.com/v4/spreadsheets/${sheet_id}/values:batchGet?ranges=A2%3AE100&valueRenderOption=FORMATTED_VALUE&key=${api_token}`);
  const data = await res.json();
  console.log(data)
  name.value = data.valueRanges[0].values[0];
  date.value = data.valueRanges[0].values[1];
  description.value = data.valueRanges[0].values[1];
  dataUrl.value = data.valueRanges[0].values[2];
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

@media (max-width: 784px) {
    .card-button {
    font-size: 1.5rem;
}
}
</style>