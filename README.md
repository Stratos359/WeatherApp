<h1>Weather App</h1>

<h2>Features</h2>

<ul>
  <li>Display weather data by buttons or date picker</li>
  <li>Visualize weather data with a chart</li>
</ul>

<h2>Installation</h2>

<ol>
  <li>Clone the repository:</li>
  <code>git clone https://github.com/Stratos359/WeatherApp.git</code>
  <li>Navigate to the project directory:</li>
  <code>cd WeatherApp</code>
  <li>Install dependencies:</li>
  <code>npm install</code>
  <li>Run the development server:</li>
  <code>npm run serve</code>
  <li>Open your browser and navigate to <a href="http://localhost:8080">http://localhost:8080</a> to view the application.</li>
</ol>

<h2>Usage</h2>

<ol>
  <li>Select a button to show current or daily weather data</li>
  <li>Select a date using the date picker to show daily weather data for the selected date.</li>
  <li>Explore the chart for a 7-day period maximum temperature forecast.</li>
</ol>

<h2>Technologies Used</h2>

<ul>
  <li>Vue.js: JavaScript framework for building user interfaces</li>
  <li>ApexCharts.js: JavaScript charting library for creating interactive charts</li>
  <li>Vue Datepicker: Vue.js datepicker component for selecting dates</li>
</ul>

<h2>Project Structure</h2>

<p>The project is organized into the following directories:</p>
<ul>
  <li><code>src/App.vue</code>: Main Vue component that serves as the entry point of the application.</li>
  <li><code>src/main.js</code>: JavaScript file that initializes the Vue application and mounts it to the DOM.</li>
  <li><code>src/components</code>: Contains Vue components for different parts of the application.</li>
  <ul>
    <li><code>WeatherInfo.vue</code>: Vue component serving as the parent/container component that encapsulates the other components and manages the overall state of the application.</li>
    <li><code>WeatherChart.vue</code>: Vue component responsible for rendering the interactive chart using ApexCharts. It receives daily weather data as props and updates the chart with the maximum temperature in a 7-day period.</li>
    <li><code>CurrentWeather.vue</code>: Vue component responsible for displaying the current weather. It receives the current weather data as props and displays them accordingly.</li>
    <li><code>DailyWeather.vue</code>: Vue component responsible for displaying the daily weather. It receives the daily weather data and the day index as props and displays the daily weather data correspoding with the day index.</li>
    <li><code>CurrentWeatherCards.vue</code>: Vue component responsible for displaying the current weather details (i.e. Feels like, Humidity etc.). It receives the current weather data as props and displays them accordingly.</li>
    <li><code>DailyWeatherCards.vue</code>: Vue component responsible for displaying the daily weather details (i.e. Feels like, Humidity etc.). It receives the daily weather data and the day index as props and displays the daily weather details corresponding with the day index.</li>
  </ul>
  <li><code>src/assets/api</code>: Contains the weatherAPI.json file </li>
</ul>

<p>Each component is responsible for a specific part of the application's user interface and functionality. They are designed to be reusable and modular, allowing for easy integration and customization within the application.</p>
