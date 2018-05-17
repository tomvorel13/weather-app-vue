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
          {{ weatherData.temp }}
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
          {{ weatherData.pressure }}
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
}

.weather-par {
  font-size: 1.6em;
  font-weight: 300;
  text-align: left;
  margin-bottom: 0;
}

.weather-par:last-child {
  padding-bottom: 2em;
}

.weather-error {
  font-size: 2em;
  font-weight: 300;
  text-align: center;
  padding: 1em 0;
}

.icon {
  width: 30px;
}

@media screen and (max-width: 830px) {
  .weather-wrapper {
    /* align-items: left; */
    margin-left: 1em;
  }
}
</style>

