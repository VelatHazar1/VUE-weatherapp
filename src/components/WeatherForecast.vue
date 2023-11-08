<template>
  <div class="forecast" v-if="forecast">
    <div class="forecast-wrap">
      <div class="day">
        <div class="date">
          {{ props.forecast.list[5].dt_txt.slice(0, -8) }}
        </div>
        <div class="temp">
          {{ Math.round(props.forecast.list[5].main.temp_min - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[5].weather[0].main }}</div>
      </div>

      <div class="day">
        <div class="date">
          {{ props.forecast.list[13].dt_txt.slice(0, -8) }}
        </div>
        <div class="temp">
          {{ Math.round(props.forecast.list[13].main.temp_ - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[13].weather[0].main }}</div>
      </div>
      <div class="day">
        <div class="date">
          {{ props.forecast.list[21].dt_txt.slice(0, -8) }}
        </div>

        <div class="temp">
          {{ Math.round(props.forecast.list[21].main.temp_ - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[21].weather[0].main }}</div>
      </div>
      <div class="day">
        <div class="date">
          {{ props.forecast.list[29].dt_txt.slice(0, -8) }}
        </div>
        <div class="temp">
          {{ Math.round(props.forecast.list[29].main.temp_ - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[29].weather[0].main }}</div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["forecast"]);
</script>
