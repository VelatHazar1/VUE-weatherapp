<template>
  <div class="forecast" v-if="forecast">
    <div class="forecast-wrap">
      <div class="day">
        {{ Math.round(props.forecast.list[5].main.temp - 273.5) }}℃
        <br />
        {{ props.forecast.list[5].dt_txt.slice(0, -8) }} <br />

        {{ props.forecast.list[5].weather[0].main }}
      </div>
      <div class="day">
        {{ Math.round(props.forecast.list[13].main.temp - 273.15) }}℃<br />
        {{ props.forecast.list[13].dt_txt.slice(0, -8) }} <br />
        {{ props.forecast.list[13].weather[0].main }} <br />
      </div>
      <div class="day">
        {{ Math.round(props.forecast.list[21].main.temp - 273.15) }}℃ <br />
        {{ props.forecast.list[21].dt_txt.slice(0, -8) }} <br />
        {{ props.forecast.list[21].weather[0].main }} <br />
      </div>
      <div class="day">
        {{ Math.round(props.forecast.list[29].main.temp - 273.15) }}℃ <br />
        {{ props.forecast.list[29].dt_txt.slice(0, -8) }} <br />
        {{ props.forecast.list[29].weather[0].main }} <br />
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["forecast"]);
</script>
