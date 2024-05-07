<template>
    <div class="chartWrapper">
        <div class="chartTitle">Weekly Variation</div>
        <apexchart height="260" type="line" :options="options" :series="series"></apexchart> <!-- Shows the ApexChart chart with data passed from the WeatherInfo component-->
    </div>
</template>

<script>
import VueApexCharts from 'vue3-apexcharts'
    export default {
        props: {
            weatherData: Object
        },
        components: {
            apexchart: VueApexCharts
        },
        data() {
                return {
                    options: {
                        chart: {
                            id: 'max-temp-weather',
                            toolbar: {
                                show: false
                            },
                            redrawnOnParentResize: true
                        },
                        line: {
                            dataLabels: {
                                position: 'top'
                            }
                        },
                        dataLabels: {
                            enabled: true,
                            style: {
                                colors: ['#616060']
                            },
                            background: {
                                enabled: false
                             },
                             offsetY: -3 
                        },
                        colors: ['#9FDF48'],
                        stroke: {
                            curve: 'smooth',
                            width: 2
                        },
                        xaxis: {
                            categories: this.weatherData.slice(0, 7).map(day => { // maps the daily dataset in a 7 day period and shows the dates
                                const date = new Date(day.dt * 1000);
                                return date.toLocaleDateString('en-GB', { month: 'numeric', day: 'numeric' });
                            }),
                        },
                        grid: {
                            xaxis: {
                                lines: {
                                    show: true
                                }
                            },
                            yaxis: {
                                lines: {
                                    show: false
                                }
                            }
                        },
                        legend: {
                            show: true,
                            showForSingleSeries: true,
                            position: 'top',
                            horizontalAlign: 'left',
                            labels: {
                                colors: ['#716F6F']
                            }
                        }
                    },
                    series: [{ 
                        name: 'Temperature',
                        data: this.weatherData.slice(0, 7).map(day => (Math.round(day.temp.max) + '°C')) // maps the daily dataset in a 7 day period and shows the max temperature
                    }]
                }
        }
    }
</script>

<style scoped>
    .chartWrapper {
        padding: 60px 15px;
    }

    .chartTitle {
        font-family: "Roboto";
        padding: 10px;
        font-size: larger;
        font-weight: bold;
    }
</style>