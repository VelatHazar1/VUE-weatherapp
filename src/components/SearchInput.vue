<template>
  <div class="search-box">
    <input
      type="text"
      class="search-bar"
      placeholder="Search..."
      v-model="query"
      @keydown.enter="handleEnterPress"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
const query = ref("");
const emit = defineEmits(["fetchWeather"]);

const handleEnterPress = () => {
  emit("fetchWeather", query.value);
};
</script>
