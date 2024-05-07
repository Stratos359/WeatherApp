
<template>
    <div class="cardWrapper">
        <div class="card">
            <div class="cardTitle">{{ Math.round(weatherData.feels_like) }}°C </div> <!-- Shows the property value from the current dataset/ In this instance the feels_like property-->
            <div class="cardSubtitle">Feels like</div>
        </div>
        <div class="card">
            <div class="cardTitle">{{ weatherData.wind_speed.toFixed(1) }} <span>m/s</span></div>
            <div class="cardSubtitle">Wind</div>
        </div>
        <div class="card">
            <div class="cardTitle"> 0 <span>m/s</span></div>
            <div class="cardSubtitle">Wind Gust</div>
        </div>
        <div class="card">
            <div class="cardTitle">{{ weatherData.wind_deg }}°</div>
            <div class="cardSubtitle">Wind Deg</div>
        </div>
        <div class="card">
            <div class="cardTitle">{{ weatherData.humidity }}<span>%</span></div>
            <div class="cardSubtitle">Humidity</div>
        </div>
        <div class="card">
            <div class="cardTitle">{{ weatherData.pressure }} <span>hPa</span></div>
            <div class="cardSubtitle">Pressure</div>
        </div>
    </div>

</template>

<script>
    export default {
        props: {
            weatherData: Object
        }
    }

</script>

<style>
    .cardWrapper {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        padding: 20px 5px;
    }

    @media (max-width: 100em) {
        .cardWrapper {
            grid-template-columns: repeat(2, 1fr);
        }
    }

    @media (max-width: 73em) {
        .cardWrapper {
            grid-template-columns: repeat(1, 1fr);
        }
    }

    .card {
        border: 2px solid whitesmoke;
        border-radius: 7%;
        padding-top: 8px;
        padding-bottom: 25px;
        padding-left: 12px;
        margin: 10px;
    }

    .cardTitle{
        font-size: x-large;
        font-weight: bold;
        font-family: "Roboto";;
        margin-top: 20px;
    }

    .cardSubtitle {
        font-family: "Roboto";
        font-weight: light;
        font-size: small;
        color: gray;
    }

    span {
        font-size: medium;
    }
</style>