
<template>
    <div class="weatherInfo">
        <div>
            <div class="title">{{ Math.round(weatherData.temp) }}°C</div> <!-- Shows the current temperature from the current dataset passed from the WeatherInfo component-->
            <div class="subtitle">{{ weatherData.weather[0].main }} - {{ weatherData.weather[0].description }}</div> <!-- Shows the main/description properties from the current dataset-->
        </div>
        <div>
            <img class="weatherIcon" :src="weatherIcon" alt="Weather Icon"> <!-- Shows the weather icon from the current dataset-->
        </div>
    </div>
    <div class="seperator-small"></div>
    <div>
        <CurrentWeatherCards :weatherData="weatherData"/> <!-- Shows the CurrentweatherCards component with passed props from the current dataset-->
    </div>
</template>

<script>
    import CurrentWeatherCards from './CurrentWeatherCards.vue'
    export default {
        props: {
            weatherData: Object
        },
        components: {
            CurrentWeatherCards
        },
        computed: {
            weatherIcon() { // returns the weather icon URL according to the icon code from the current dataset
                const iconCode = this.weatherData.weather[0].icon;
                return `https://openweathermap.org/img/wn/${iconCode}.png`
            }
        }
    }
    
</script>

<style>
    .weatherInfo {
        display: flex;
        justify-content: space-between;
        padding: 25px 0;
        height: 120px;
    }

    .weatherIcon {
        height: 100px;
    }

    .title {
        font-size: 45px;
        font-weight: bold;
        font-family: "Roboto";
        margin-top: 20px;
    }

    .subtitle {
        font-family: "Roboto";
        font-weight: light;
        font-size: small;
        color: gray;
    }

    .seperator-small {
      height: 5px;
      background-color: whitesmoke;
      margin-left: -28px;
      margin-right: -28px;
    }
</style>