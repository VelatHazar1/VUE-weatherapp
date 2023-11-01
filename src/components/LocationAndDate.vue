<template>
  <div class="location-box">
    <div class="location">
      {{ props.weather.name }}, {{ props.weather.sys.country }}
    </div>
    <div class="date">{{ props.date }}</div>
  </div>
</template>
<script setup>
const props = defineProps(["weather", "date"]);
</script>
