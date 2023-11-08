<template>
  <div class="forecast" v-if="forecast">
    <div class="forecast-wrap">
      <div class="day">
        <div class="date">
          {{ nextFourDays[0] }}
        </div>
        <div class="temp">
          {{ Math.round(props.forecast.list[5].main.temp_min - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[5].weather[0].main }}</div>
      </div>

      <div class="day">
        <div class="date">
          {{ nextFourDays[1] }}
        </div>
        <div class="temp">
          {{ Math.round(props.forecast.list[13].main.temp_min - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[13].weather[0].main }}</div>
      </div>
      <div class="day">
        <div class="date">
          {{ nextFourDays[2] }}
        </div>

        <div class="temp">
          {{ Math.round(props.forecast.list[21].main.temp_min - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[21].weather[0].main }}</div>
      </div>
      <div class="day">
        <div class="date">
          {{ nextFourDays[3] }}
        </div>
        <div class="temp">
          {{ Math.round(props.forecast.list[29].main.temp_min - 273.5) }}℃
        </div>
        <div class="weather">{{ props.forecast.list[29].weather[0].main }}</div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["forecast"]);
const nextFourDays = [];
const getNextFourDays = () => {
  const currentDate = new Date();
  const days = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday",
  ];

  for (let i = 1; i < 5; i++) {
    const nextDate = new Date(currentDate);
    nextDate.setDate(currentDate.getDate() + i);

    const day = days[nextDate.getDay()];

    const dateString = `  ${day}  `;
    nextFourDays.push(dateString);
  }

  return nextFourDays;
};

const nextFourDaysArray = getNextFourDays();
console.log(nextFourDaysArray);
</script>
