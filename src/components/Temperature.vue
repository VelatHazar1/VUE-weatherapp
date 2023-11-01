<template>
  <div class="weather-box">
    <div class="temperature">{{ Math.round(props.weather.main?.temp) }}°c</div>
    <div class="weather">{{ props.weather.weather[0]?.main }}</div>
  </div>
</template>
<script setup>
const props = defineProps(["weather"]);
</script>
