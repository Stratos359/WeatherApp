<template>
    <div class="weatherInfo">
        <div>
            <div class="title">{{ Math.round((weatherData[dayIndex].temp.day + weatherData[dayIndex].temp.night)/2) }}°C</div> <!-- Shows the daily temperature as a median of the day and night properties from the daily dataset passed from the WeatherInfo component-->
            <div class="subtitle">{{ weatherData[dayIndex].weather[0].main }} - {{ weatherData[dayIndex].weather[0].description }}</div> <!-- Shows the main/description properties from the daily dataset-->
        </div>
        <div>
           <img class="weatherIcon" :src="weatherIcon" alt="Weather Icon"> <!-- Shows the weather icon from the daily dataset-->
        </div>
    </div>
    <div class="seperator-small"></div>
    <div class="weatherCards">
        <DailyWeatherCards :weatherData="weatherData" :dayIndex="dayIndex"/> <!-- Shows the DailyWeatherCards component with passed props from the daily dataset-->
    </div>
</template>

<script>
import DailyWeatherCards from './DailyWeatherCards.vue';
    export default {
        props: {
            weatherData: Object,
            dayIndex: Number,
        },
        components: {
            DailyWeatherCards
        },
        computed: {
            weatherIcon() { // returns the weather icon URL according to the icon code from the current dataset
                const iconCode = this.weatherData[this.dayIndex].weather[0].icon;
                return `http://openweathermap.org/img/wn/${iconCode}.png`
            }
        }
    }
</script>