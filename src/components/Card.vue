<template>
    <div class="cards" style="display: flex">
        <div class="card">
            <div class="weather-wrap" v-if ="typeof weather.main != 'undefined' " >
            <div class="container location-box">
            <div class="location"> {{ weather.name }} , {{ weather.sys.country }}</div>
            <div class="date"> {{ dateBuilder() }}</div>
            </div>
            <div class="weather-box">
            <div class="weather"><img: src="`https://openweathermap.org/img/wn/${weather.weather[0].icon}@2x.png`" alt="weather" /></div>
            <div class="temp"> {{ Math.round(weather.main.temp)}} °C</div>
            </div>
        </div>
  </div>
</div>
</template>

<style>
     @import "../assets/css/App.css";
</style>

<script>
    import '../App.vue';
</script>
