<template>
    <div class="cardWrapper">
        <div class="card">
            <div class="cardTitle">{{ Math.round((weatherData[dayIndex].feels_like.day + weatherData[dayIndex].feels_like.night)/2) }}°C </div> <!-- Shows the property value from the daily dataset/ In this instance the median between the day and night feels_like properties-->
            <div class="cardSubtitle">Feels like</div>
        </div>
        <div class="card">
            <div class="cardTitle">{{ weatherData[dayIndex].wind_speed.toFixed(1) }} <span>m/s</span></div>
            <div class="cardSubtitle">Wind</div>
        </div>
        <div class="card">
            <div class="cardTitle">{{ weatherData[dayIndex].wind_gust.toFixed(1) }} <span>m/s</span></div>
            <div class="cardSubtitle">Wind Gust</div>
        </div>
        <div class="card">
            <div class="cardTitle">{{ weatherData[dayIndex].wind_deg }}°</div>
            <div class="cardSubtitle">Wind Deg</div>
        </div>
        <div class="card">
            <div class="cardTitle">{{ weatherData[dayIndex].humidity }}<span>%</span></div>
            <div class="cardSubtitle">Humidity</div>
        </div>
        <div class="card">
            <div class="cardTitle">{{ weatherData[dayIndex].pressure }} <span>hPa</span></div>
            <div class="cardSubtitle">Pressure</div>
        </div> 
    </div>
</template>

<script>
    export default {
        props: {
            weatherData: Object,
            dayIndex: Number
        }
    }
</script>