<template>
  <div>
    <div v-if="forecast">
      <h2>Weather Forecast for the Next Four Days</h2>
      <div v-for="dayForecast in nextFourDays" :key="dayForecast.date">
        <h3>{{ dayForecast.dayName }}</h3>
        <p>Date: {{ dayForecast.date }}</p>
        <p>Temperature: {{ dayForecast.main.temp }}°C</p>
        <!-- Display other weather data as needed -->
      </div>
    </div>
  </div>
</template>

<script setup>
// ... Your existing setup code ...

const nextFourDays = computed(() => {
  if (forecast) {
    const currentDate = new Date();
    const daysOfWeek = [
      "Sunday",
      "Monday",
      "Tuesday",
      "Wednesday",
      "Thursday",
      "Friday",
      "Saturday",
    ];

    const fourDayForecasts = forecast.list
      .filter((item) => {
        const itemDate = new Date(item.dt * 1000);
        return itemDate > currentDate;
      })
      .slice(0, 4);

    return fourDayForecasts.map((item) => {
      const itemDate = new Date(item.dt * 1000);
      const dayName = daysOfWeek[itemDate.getDay()];
      return {
        dayName,
        date: itemDate.toLocaleDateString(),
        main: item.main,
        // Include other forecast data here if needed
      };
    });
  }
  return [];
});
</script>
