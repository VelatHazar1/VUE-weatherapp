<template>
  <div class="forecast">
    <div class="forecast-wrap">
      <p>{{ forecast }}</p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["forecast"]);
</script>
