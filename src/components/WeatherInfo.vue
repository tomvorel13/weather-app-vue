<template>
  <div class="weather-info">
    <div v-if="weatherData.city">
        <p class="weather-par animated slideInRight">
          <span class="icon">
            <i class="far fa-building" /> 
          </span>
          {{ weatherData.city }}
        </p>
        <p class="weather-par animated slideInRight"> 
          <span class="icon">
            <i class="fas fa-globe" /> 
          </span>
          {{ weatherData.country }}
        </p>
        <p class="weather-par animated slideInRight">
          <span class="icon">
            <i class="fas fa-thermometer-half" />
          </span>
          {{ Math.round(weatherData.temp) }} °C
        </p>
        <p class="weather-par animated slideInRight">
          <span class="icon">
            <i class="fas fa-comment" />
          </span>
          {{ weatherData.desc }}
        </p>
        <p class="weather-par animated slideInRight">
          <span class="icon">
            <i class="fas fa-tachometer-alt" />
          </span>
          {{ weatherData.pressure }} hPa
        </p>
     </div>   
     <h2 v-if="weatherData.error" class="weather-error animated slideInRight">
        <span class="icon">
          <i class="fas fa-exclamation-triangle" /> 
        </span>
        I was not able to find that city :-(
      </h2>
  </div>
  
</template>

<script>
export default {
  name: 'WeatherInfo',
  props: ['weatherData']
}
</script>

<style>
.weather-info {
  padding: 0 3em;
  display: flex;
  flex-direction: column;
  color: #4fc08d;
}

.weather-info .weather-par {
  font-size: 1.6em;
  font-weight: 300;
  text-align: left;
  margin-bottom: 0;
}

.weather-info .weather-par:last-child {
  padding-bottom: 2em;
}

.weather-info .weather-error {
  font-size: 2em;
  font-weight: 300;
  text-align: center;
  padding: 1em 0;
}

.weather-info .icon {
  color: #4fc08d;
  width: 30px;
  display: inline-block;
  margin: 0 20px 7px 0;
}

@media screen and (max-width: 830px) {
  .weather-info .weather-wrapper {
    margin-left: 1em;
  }
}
</style>

