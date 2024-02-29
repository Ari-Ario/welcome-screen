<script setup>
import {onBeforeMount, onMounted, ref} from 'vue';
import welcome from './welcome.vue'
import day from './theDay.vue'
import info from './infoBlock.vue'
const sheet_id = import.meta.env.VITE_GOOGLE_SHEET_ID;
const api_token = import.meta.env.VITE_GOOGLE_API_KEY;

// Today: 
const date = new Date();
let currentDay= String(date.getDate()).padStart(2, '0');
let currentMonth = String(date.getMonth()+1).padStart(2,"0");
let currentYear = date.getFullYear();

// we will display the date as DD-MM-YYYY 

let currentDate = `${currentDay}.${currentMonth}.${currentYear}`;

const dateDB = ref("")
const time = ref("")
const description = ref("")
const address = ref("")
const newRow = ref("")

async function fetchData() {
  const res = await fetch(`https://sheets.googleapis.com/v4/spreadsheets/${sheet_id}/values:batchGet?ranges=A2%3AE100&valueRenderOption=FORMATTED_VALUE&key=${api_token}`);
  const fetchedData = await res.json();
  let data= fetchedData.valueRanges[0].values
  for(let i=0; i<=data.length; i++){

    if (data[i][1] === currentDate){
      time.value = data[i][0];
      dateDB.value = data[i][1];
      description.value = data[i][2];
      address.value = data[i][3];
    }
  }
}
const allData= fetchData() 
</script>

<template>
  <div class="user-container">
    <welcome />
    <day :day="dateDB" />
      <div class="info-container">
        <info :info="time" :descritpion="description" :address="address"/>
        <!-- <info :info="description" />
        <info class="user-email" :info="address" /> -->
        <button class="card-button" @click="fetchData()">Next</button>
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