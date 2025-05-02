<script setup>
import { ref, watch } from 'vue'
const props = defineProps({
  prefecture: String
})
const APIKey = 'ca68769c1b94a4eb0df6bd509adeac67'
const weather = ref('') //天気
const temperature = ref('') //気温
const icon = ref('') //天気アイコン

watch(() => props.prefecture, async (city) => {
  if (!city) return
  try {
    const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${APIKey}&units=metric&lang=ja`)
    const data = await response.json()

    weather.value = data.weather[0].description

    temperature.value = data.main.temp
    icon.value = `http://openweathermap.org/img/wn/${data.weather[0].icon}@2x.png`
  } catch (error) {
    console.error('APIエラー:', error)
  }
})
</script>
<template>
<div class="">
    <p>{{ weather }}</p>
    <img :src="icon" alt="">
    <p v-if="temperature">気温 : {{ temperature }}°</p>
</div>
</template>
<style scoped>

</style>