<template>
  <div class="forecast" v-if="forecast">
    <div class="forecast-wrap">
      <div class="day">
        <div class="date">
          {{ props.forecast.list[12].dt_txt.slice(0, -8) }}
        </div>
        <div class="temp">
          {{ Math.round(props.forecast.list[12].main.temp - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[12].weather[0].main }}</div>
      </div>

      <div class="day">
        <div class="date">
          {{ props.forecast.list[20].dt_txt.slice(0, -8) }}
        </div>
        <div class="temp">
          {{ Math.round(props.forecast.list[20].main.temp - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[20].weather[0].main }}</div>
      </div>
      <div class="day">
        <div class="date">
          {{ props.forecast.list[28].dt_txt.slice(0, -8) }}
        </div>

        <div class="temp">
          {{ Math.round(props.forecast.list[28].main.temp - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[28].weather[0].main }}</div>
      </div>
      <div class="day">
        <div class="date">
          {{ props.forecast.list[36].dt_txt.slice(0, -8) }}
        </div>
        <div class="temp">
          {{ Math.round(props.forecast.list[36].main.temp - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[36].weather[0].main }}</div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["forecast"]);
</script>
