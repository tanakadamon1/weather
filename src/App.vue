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
