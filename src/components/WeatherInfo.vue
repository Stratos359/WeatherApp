<template>
    <div class="wrapper">
        <div class="menu">
            <button @click="showCurrentWeather" class="button" :class="{ active: currentWeather }">Now</button> <!-- Button that shows the CurrentWeather component -->
            <button @click="showDailyWeather" class="button" :class="{ active: !currentWeather&&selectedDate===null }">Today</button> <!-- Button that shows the DailyWeather component -->
            <VueDatePicker v-model="selectedDate" placeholder="Select Date" :format="format" :min-date="new Date()" :max-date="maxDate" :enable-time-picker="false" auto-apply/> <!-- Datepicker that passes the selected date to the DailyWeather component-->
        </div>
    
        <div v-if="weatherData">
    
          <div v-if="currentWeather">
              <CurrentWeather :weatherData="weatherData.current"/> <!-- CurrentWeather component-->
          </div>
          <div v-else>
              <DailyWeather :weatherData="weatherData.daily" :dayIndex="calculateDayIndex"/> <!-- DailyWeather component-->
          </div>
          <div class="seperator"></div>
          <div class="weatherChart">
            <WeatherChart :weatherData="weatherData.daily"/> <!-- WeatherChart component that displays the max temperatures from the weatherData in a 7 day period-->
          </div>
        </div>
    </div>
  </template>
  
  <script>
  import weatherAPI from '../assets/api/weatherAPI.json'
  import VueDatePicker  from '@vuepic/vue-datepicker'
  import '@vuepic/vue-datepicker/dist/main.css'
  import CurrentWeather from '../components/CurrentWeather'
  import DailyWeather from '../components/DailyWeather'
  import WeatherChart from './WeatherChart.vue'

  export default {
    data() {
      return {
        weatherData: weatherAPI,
        currentWeather: true,
        maxDate: null,
        selectedDate: null,
        dayIndex: 0,
        format: 'dd-MM-yyyy',
      };
    },
    components: {
        CurrentWeather,
        DailyWeather,
        VueDatePicker,
        WeatherChart
    },
    mounted() {
      this.setMaxDate();
    },
    methods: {
  
      showCurrentWeather() { // show the CurrentWeather component / return the selectedDate to null if user has selected a date from the datepicker
        this.currentWeather = true;
        this.selectedDate = null;
      },
      showDailyWeather() { // show the DailyWeather component / return the selectedDate to null if user has selected a date from the datepicker
        if(!this.currentWeather){
            this.selectedDate = null;
        }
        this.currentWeather = false;
      },
      setMaxDate() {
        const maxDate = new Date();
        maxDate.setDate(maxDate.getDate()+6)
        this.maxDate = maxDate;
      },
    },
    computed: {
        calculateDayIndex(){ // returns the dayIndex passed as prop to the DailyWeather component / if selectedDate is null it passes the dayIndex corresponding to the current daily dataset
            if(this.selectedDate === null){
                return(this.dayIndex);
            }
            else{
                const today = new Date();
                const selectedDay = new Date(this.selectedDate);
                const diffDays = Math.ceil((selectedDay - today) / (1000 * 3600 * 24));
                return(diffDays);
            }
        }
    },
    watch: { // watches for a change in the selectedDate from the datepicker and shows the apropriate component 
        selectedDate() {
            if(!(this.selectedDate === null && this.currentWeather) ){
                this.currentWeather = false;
            }
        }
    }

  };
  </script>
  
  <style scoped>
    .button {
        font-size: 14px;
        font-family: "Roboto";
        padding: 9px 16px;
        margin-right: 13px;
        border-radius: 10%;
        border: 1px solid lightgray;
    }

    .button:hover {
        cursor: pointer;
    }

    .active {
        color: #94D076;
        background: #E0F4D6;
        border: 1px solid #94D076;
    }

    .menu {
        display: flex;
        max-width: 55%;
    }

    .wrapper {
        max-width: 30%;
        margin: auto;
        padding: 30px;
        border-radius: 1%;
        box-shadow: 0 0 10px 5px whitesmoke;
        
    }

    .seperator {
      height: 23px;
      background-color: whitesmoke;
      margin-left: -28px;
      margin-right: -28px;
    }
  </style>
