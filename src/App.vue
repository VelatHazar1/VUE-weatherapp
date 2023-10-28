<script>
import { ref } from "vue";

export default {
  setup() {
    const apiKey = "842427aa8747da82d264ea98b46d2a19";
    const baseUrl = "https://api.openweathermap.org/data/2.5/";
    const query = ref("");
    const weather = ref({});

    const fetchWeather = (e) => {
      if (e.key === "Enter") {
        fetch(`${baseUrl}weather?q=${query.value}&units=metric&APPID=${apiKey}`)
          .then((res) => res.json())
          .then(setResults);
      }
    };

    const setResults = (results) => {
      weather.value = results;
    };

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
      const date = d.getDate();
      const month = months[d.getMonth()];
      const year = d.getFullYear();

      return ` ${date} ${month} ${day} ${year}`;
    };

    return {
      apiKey,
      baseUrl,
      query,
      weather,
      fetchWeather,
      setResults,
      dateBuilder,
    };
  },
};
</script>
<template>
  <div
    id="app"
    :class="
      typeof weather.main != 'undefined' && weather.main.temp > 16 ? 'warm' : ''
    "
  >
    <main>
      <div class="search-box">
        <input
          type="text"
          class="search-bar"
          placeholder="Search..."
          v-model="query"
          @keypress="fetchWeather"
        />
      </div>

      <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
        <div class="location-box">
          <div class="location">
            {{ weather.name }}, {{ weather.sys.country }}
          </div>
          <div class="date">{{ dateBuilder() }}</div>
        </div>

        <div class="weather-box">
          <div class="temperature">{{ Math.round(weather.main.temp) }}°c</div>
          <div class="weather">{{ weather.weather[0].main }}</div>
        </div>
      </div>
    </main>
  </div>
</template>
