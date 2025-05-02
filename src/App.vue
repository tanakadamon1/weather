<script setup>
import { ref, watchEffect } from "vue"
import SearchForm from "./components/searchForm.vue"
import weatherCard from "./components/weatherCard.vue"

const prefecture = ref('')
watchEffect(() => {
  console.log(prefecture.value)
})
</script>

<template>
  <h1>天気アプリ</h1>
  <SearchForm v-model:prefecture="prefecture" />
  <weatherCard v-model:prefecture="prefecture" />
</template>

<style>
*, *::after, *::before{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app{
  max-width: 1000px;
  margin: 36px auto;
}
</style>
