<template>
  <div id="app">
    <div class="flex-container">
      <div class="heading-wrapper">
        <h1>WeatherAPP VUE</h1>
        <p class="lead-sentence">
          Find the latest weather conditions in your city
        </p>
        <p class="instructions">
          1. Enter the city name <br/>
          2. Enter the country acronym e.g. US <br/>
          3. Click "Get weather"
        </p>
    </div>
    <SearchBar 
      :fetchWeather="fetchWeather"
      :clearData="clearData"
      :userInput="this.userInput"
    />
    </div>
    <WeatherInfo
      :weatherData="this.weatherData"
    />
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from '@/components/SearchBar.vue'
import WeatherInfo from '@/components/WeatherInfo.vue'

const API_KEY = 'c5c58670c32db956ece142ae13d1759f'

export default {
  name: 'app',
  components: {
    SearchBar,
    WeatherInfo
  },
  data() {
    return {
      weatherData: {
        city: null,
        country: null,
        temp: null,
        desc: null,
        pressure: null,
        error: null
      },
      userInput: {
        city: null,
        country: null
      }
    }
  },
  methods: {
    fetchWeather() {
      let city = this.userInput.city
      let country = this.userInput.country
      axios
        .get(
          `https://api.openweathermap.org/data/2.5/weather?APPID=${API_KEY}&q=${city},${country}&units=metric`
        )
        .then(res => {
          let data = res.data
          this.weatherData.city = data.name
          this.weatherData.country = data.sys.country
          this.weatherData.temp = data.main.temp
          this.weatherData.desc = data.weather[0].description
          this.weatherData.pressure = data.main.pressure
          this.weatherData.error = null
        })
        .catch(err => {
          this.weatherData.city = null
          this.weatherData.country = null
          this.weatherData.temp = null
          this.weatherData.desc = null
          this.weatherData.pressure = null
          this.weatherData.error = err.message
        })

      this.userInput.city = null
      this.userInput.country = null
    },

    clearData() {
      this.weatherData.city = null
      this.weatherData.country = null
      this.weatherData.temp = null
      this.weatherData.desc = null
      this.weatherData.pressure = null
      this.weatherData.error = null

      document.getElementById('myForm').reset()
    }
  }
}
</script>

<style>
#app {
  max-width: 880px;
  margin: 5em auto 0 auto;
  border-radius: 10px;
  font-family: 'Lato', sans-serif;
  color: black;
  box-shadow: 6px 4px 20px 0px rgba(189, 189, 189, 1);
}

#app .flex-container {
  display: flex;
  justify-content: space-between;
}

#app .heading-wrapper {
  -webkit-clip-path: polygon(0 0, 100% 0, 75% 100%, 0% 100%);
  clip-path: polygon(0 0, 100% 0, 75% 100%, 0% 100%);
  background-color: #4fc08d;
  width: 50%;
  padding: 1em 3em;
  color: white;
}

#app h1 {
  font-size: 3em;
  font-weight: 300;
  margin-top: 0;
}

#app .lead-sentence {
  font-weight: 300;
  font-size: 1.2em;
}

#app .instructions {
  font-style: italic;
  font-weight: 300;
}

/* MEDIA QUERIES */

@media screen and (max-width: 830px) {
  #app .wrapper {
    margin-top: 0;
  }

  #app .flex-container {
    flex-direction: column;
    align-items: center;
  }

  #app .heading-wrapper {
    -webkit-clip-path: none;
    clip-path: none;
    width: 90%;
    padding: 2em 1em;
  }

  #app h1 {
    font-size: 2em;
    text-align: center;
  }

  #app .lead-sentence,
  #app .instructions {
    text-align: center;
  }
}
</style>
