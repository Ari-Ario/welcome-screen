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

let currentDate = ref(`${currentDay}.${currentMonth}.${currentYear}`);

const data = ref("")
const dateDB = ref("")
const timeInterval = ref("")

async function fetchData() {
  const res = await fetch(`https://sheets.googleapis.com/v4/spreadsheets/${sheet_id}/values:batchGet?ranges=A2%3AE100&valueRenderOption=FORMATTED_VALUE&key=${api_token}`);
  const fetchedData = await res.json();
  data.value= fetchedData.valueRanges[0].values

   for(let i=0; i<=data.value.length; i++){
      dateDB.value = fetchedData.valueRanges[0].values[i][1]
    }
  }

fetchData()
onMounted( () => {
  timeInterval.value = setInterval(() => {
    fetchData()
  }
  , 1000*60*30)
});

</script>

<template>
  <div class="user-container">
    <welcome />
    <day :day="currentDate" />
      <div v-for="(row, index) in data" class="info-container" :key="index">
        <info :time="row[0]" :descritpion="row[2]" :address="row[3]"/>
        <!-- <button class="card-button" @click="fetchData()">Next</button> -->
      </div>
    </div>
</template>

<style scoped>
.user-container {
  display: block;
  top: 0;
  text-align: center;
  font-size: 1.5rem;
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