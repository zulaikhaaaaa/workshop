<script setup>
import HelloWorld from './components/HelloWorld.vue'
import {ref} from 'vue'

let count = ref(0);
let input = ref("")

function Increment(){
  count.value +=1
}
function Decrement(){
  count.value -=1
}
</script>

<template>
    <div>
      <p>{{ count }}</p>
      <button @click="Increment">Increment</button>
      <button @click="Decrement">Decrement</button>
      
    </div>
</template>

<style scoped>

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em red);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em green);
}
</style>





<script setup>
import {ref, onMounted} from 'vue'

let prayerTimes = ref([])

onMounted(async function(){

  let response = await fetch('https://www.e-solat.gov.my/index.php?r=esolatApi/TakwimSolat&period=today&zone=WLY01')
  let data = await response.json()
  prayerTimes.value = data.prayerTime
  console.log(data.prayerTime)
})

</script>

<template>
<div></div>
  <div v v-for="time in prayerTimes">
    <p class="text-x1">{{ time.hijri }}</p>
    <p class="text-x1">{{ time.date }}</p>
    <p class="text-x1">{{ time.day }}</p>
    <p class="text-x1">{{ time.imsak }}</p>
    <p class="text-x1">{{ time.fajr }}</p>
    <p class="text-x1">{{ time.syuruk }}</p>
    <p class="text-x1">{{ time.dhuhr }}</p>
    <p class="text-x1">{{ time.asr }}</p>
    <p class="text-x1">{{ time.maghrib }}</p>
    <p class="text-x1">{{ time.isha }}</p>
  </div>

  <!--<table class="table">
    <thead>
      <tr>
        <th>Hijri</th>
        <th>Date</th>
        <th>Day</th>
        <th>Imsak</th>
        <th>Fajr</th>
        <th>Syuruk</th>
        <th>Dhuhr</th>
        <th>Asr</th>
        <th>Maghrib</th>
        <th>Isha</th>
      </tr>
    </thead>
  </table>
    <tr v-for="prayerTime in prayerTimes">
      <td></td>
    </tr>-->
</template>

<style scoped>

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em red);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em green);
}
</style>
