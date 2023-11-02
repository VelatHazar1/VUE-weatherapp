<script setup>
import { ref } from "vue";
import SearchInput from "./components/SearchInput.vue";
import Temperature from "./components/Temperature.vue";
import LocationAndDate from "./components/LocationAndDate.vue";
import WeatherForecast from "./components/WeatherForecast.vue";

const apiKey = "842427aa8747da82d264ea98b46d2a19";
const baseUrl = "https://api.openweathermap.org/data/2.5/";
const forecast = ref();
const weather = ref();
const date = ref();

const fetchWeather = (e) => {
  fetch(`${baseUrl}weather?q=${e}&units=metric&APPID=${apiKey}`)
    .then((res) => res.json())
    .then(setResults);
  fetch(`${baseUrl}forecast?q=${e}&appid=${apiKey}`)
    .then((res) => res.json())
    .then(setForecast);

  dateBuilder();
};

const setResults = (results) => {
  weather.value = results;
};
const setForecast = (results) => {
  forecast.value = results;
};

//FIXME: toLocalTimeString
const dateBuilder = () => {
  const d = new Date();
  const months = [
    "January",
    "February",
    "March",
    "April",
    "May",
    "June",
    "July",
    "August",
    "September",
    "October",
    "November",
    "December",
  ];
  const days = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday",
  ];

  const day = days[d.getDay()];
  const event = d.getDate();
  const month = months[d.getMonth()];
  const year = d.getFullYear();

  date.value = ` ${event} ${month} ${day} ${year}`;
};
</script>
<template>
  <div
    id="app"
    :class="
      typeof weather?.main != 'undefined' && weather?.main.temp > 16
        ? 'warm'
        : ''
    "
  >
    <main>
      <SearchInput @fetch-weather="fetchWeather"></SearchInput>
      <LocationAndDate
        :weather="weather"
        :date="date"
        v-if="weather"
      ></LocationAndDate>
      <div class="weather-wrap">
        <Temperature :weather="weather" v-if="weather"></Temperature>
        <WeatherForecast :forecast="forecast"></WeatherForecast>
      </div>
    </main>
  </div>
</template>
