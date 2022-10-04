<template>
    <div>
    <h1>My Weather App</h1>
    <button v-on:click="getWeatherData">Get Weather Data</button>
    <div v-for="weatherData in weatherDataList" :key="weatherData.id" class="weather-data">
      <div class="weather-stats">
        <div>
          <span>{{weatherData.time}}</span>
        </div>
        <div>
          <span class="location">{{weatherData.location}}</span>
        </div>
      </div>
      <div class="weather-temp">
        <span>{{weatherData.temp}}°</span>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        data () {
            return {
                weatherDataList: []
            };
        },
        methods: {
            getWeatherData () {
                fetch("https://musaubrian.github.io/host-js/data/weather.json")
                .then(Response => Response.json())
                .then(data => (this.weatherDataList = data));
            }
        }
    }


</script>

<style>
.weather-data {
  display: flex;
  align-items: center;
  margin-top: 20px;
  margin-left: 20px;
  border-bottom: 2px solid #ccc;
  padding: 20px;
}

.weather-stats {
  flex-grow: 8;
  text-align: left;
  padding-left: 20px;
}

.weather-stats .location {
  font-size: 30px;
}

.weather-temp {
  flex-grow: 1;
  font-size: 35px;
}

img {
  width: 70px;
}
</style>