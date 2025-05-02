<script setup>
import { ref, watch } from 'vue'
const props = defineProps({
  prefecture: String
})
const APIKey = 'ca68769c1b94a4eb0df6bd509adeac67'
const weather = ref('') //天気
const temperature = ref('') //現在の気温
const icon = ref('') //天気アイコン
const forecastList = ref([]) //5日間の天気

watch(() => props.prefecture, async (city) => {
  if (!city) return
  try {
    const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${APIKey}&units=metric&lang=ja`)
    const data = await response.json()
    weather.value = data.weather[0].description

    temperature.value = data.main.temp
    icon.value = `http://openweathermap.org/img/wn/${data.weather[0].icon}@2x.png`


    // 5日間の天気
    const forecastRes = await fetch(`https://api.openweathermap.org/data/2.5/forecast?q=${city}&appid=${APIKey}&units=metric&lang=ja`)
    const forecastData = await forecastRes.json()
    forecastList.value = filterNoonForecasts(forecastData.list)
    console.log(forecastList.value)
  } catch (error) {
    console.error('APIエラー:', error)
  }
})
function filterNoonForecasts(forecastList) {
  return forecastList.filter(item => item.dt_txt.includes("12:00:00"))
}
</script>
<template>
<div class="">
    <div v-if="weather" class="day">
        <p>{{ weather }}</p>
        <img :src="icon" alt="">
        <p v-if="temperature">現在の気温 : {{ temperature }}℃</p>
    </div>

    <div v-if="forecastList.length">
  <h2>12時の天気予報（5日分）</h2>
  <ul>
    <li v-for="(item, index) in forecastList" :key="index">
      {{ item.dt_txt.split(' ')[0] }}：{{ item.weather[0].description }}（{{ item.main.temp }}℃）
    </li>
  </ul>
</div>

</div>
</template>
<style scoped>
.day{
    border: 1px solid #333;
    box-shadow: 4px 4px 6px #3333333a;
    max-width: 260px;
    text-align: center;
    margin-top: 24px;
    border-radius: 8px;
    padding: 8px;
}
h2{
    margin-top: 36px;
    margin-bottom: 24px;
}
li{
    list-style: none;
    margin-bottom: 8px;
}
</style>