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
    <SearchBar />
    </div>
    <WeatherInfo />
  </div>
</template>

<script>
import SearchBar from '@/components/SearchBar.vue'
import WeatherInfo from '@/components/WeatherInfo.vue'

export default {
  name: 'app',
  components: {
    SearchBar,
    WeatherInfo
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

.flex-container {
  display: flex;
  justify-content: space-between;
}

.heading-wrapper {
  -webkit-clip-path: polygon(0 0, 100% 0, 75% 100%, 0% 100%);
  clip-path: polygon(0 0, 100% 0, 75% 100%, 0% 100%);
  background-color: #4fc08d;
  width: 50%;
  padding: 1em 3em;
  color: white;
}

h1 {
  font-size: 3em;
  font-weight: 300;
  margin-top: 0;
}

.lead-sentence {
  font-weight: 300;
  font-size: 1.2em;
}

.instructions {
  font-style: italic;
  font-weight: 300;
}

/* MEDIA QUERIES */

@media screen and (max-width: 830px) {
  .wrapper {
    margin-top: 0;
  }

  .flex-container {
    flex-direction: column;
  }

  .heading-wrapper {
    -webkit-clip-path: none;
    clip-path: none;
    width: 90%;
    padding: 2em 1em;
  }

  h1 {
    font-size: 2em;
    text-align: center;
  }

  .lead-sentence,
  .instructions {
    text-align: center;
  }
}
</style>
