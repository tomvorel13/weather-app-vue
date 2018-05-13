<template>
  <div class="weather-info">
        <p class="weather-par animated slideInRight">
          <span class="icon">
            <i class="far fa-building" />
          </span>
        </p>
        <p class="weather-par animated slideInRight">
          <span class="icon">
            <i class="fas fa-globe" />
          </span>
        </p>
        <p class="weather-par animated slideInRight">
          <span class="icon">
            <i class="fas fa-thermometer-half" />
          </span>
        </p>
        <p class="weather-par animated slideInRight">
          <span class="icon">
            <i class="fas fa-comment" />
          </span>
        </p>
        <p class="weather-par animated slideInRight">
          <span class="icon">
            <i class="fas fa-tachometer-alt" />
          </span>
        </p>
        <h2 class="weather-error animated slideInRight">
          <span class="icon">
            <i class="fas fa-exclamation-triangle" />
          </span>
        </h2>
  </div>
</template>

<script>
export default {
  name: 'WeatherInfo',
  data() {
    return {}
  }
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

