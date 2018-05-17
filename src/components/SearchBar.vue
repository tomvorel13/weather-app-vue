<template>
  <div class="searchbar">   
      <form @submit.prevent="fetchWeather" id="myForm">
        <div class="input-wrapper">
          <span class="icon">
            <i class="far fa-building" />
          </span>
          <input
            class="field"
            type="text"
            v-model="userInput.city"
            placeholder="City"
          />
        </div>
        <div class="input-wrapper">
          <span class="icon">
            <i class="fas fa-globe" />
          </span>
          <input
            class="field"
            type="text"
            v-model="userInput.country"
            placeholder="Country"
          />
        </div>

        <br />
        <button class="btn btn-effect">Get weather</button>
      </form>
      <button @click="clearData" class="btn btn-effect">
        Clear
      </button>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  props: ['fetchWeather', 'clearData', 'userInput']
}
</script>

<style>
.searchbar {
  display: flex;
  flex-direction: column;
  justify-content: center;
  max-width: 300px;
  padding: 1em 3em;
}

.searchbar .btn {
  display: inline-block;
  border: 2px solid #4fc08d;
  background-color: white;
  color: #4fc08d;
  font-size: 1em;
  padding: 5px 0px;
  border-radius: 100px;
  width: 100%;
  margin: 5px 0;
  outline: none;
  overflow: hidden;
}

.searchbar .icon {
  color: #4fc08d;
  width: 30px;
  display: inline-block;
  margin-bottom: 7px;
}

.searchbar .btn:hover {
  cursor: pointer;
}

.searchbar .btn:focus {
  outline: none;
}

.searchbar .field {
  outline: none;
  font-size: 1.2em;
  padding: 5px 10px;
  margin-bottom: 5px;
  width: 92%;
  background: transparent;
  border: none;
  color: #4fc08d;
  text-shadow: 0;
  border-bottom: 2px solid transparent;
}

.searchbar .field:focus {
  border-bottom: 2px solid #4fc08d;
}

.searchbar ::placeholder {
  color: #4fc08d;
  opacity: 1;
}

.searchbar input:focus::-webkit-input-placeholder {
  color: transparent;
}
.searchbar input:focus:-moz-placeholder {
  color: transparent;
} /* FF 4-18 */
.searchbar input:focus::-moz-placeholder {
  color: transparent;
} /* FF 19+ */
.searchbar input:focus:-ms-input-placeholder {
  color: transparent;
} /* IE 10+ */

/* Hover buttons */
.searchbar .btn-effect {
  display: inline-block;
  vertical-align: middle;
  -webkit-transform: perspective(1px) translateZ(0);
  transform: perspective(1px) translateZ(0);
  box-shadow: 0 0 1px rgba(0, 0, 0, 0);
  position: relative;
  background: white;
  -webkit-transition-property: color;
  transition-property: color;
  -webkit-transition-duration: 0.3s;
  transition-duration: 0.3s;
}
.searchbar .btn-effect:before {
  content: '';
  position: absolute;
  z-index: -1;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: #4fc08d;
  -webkit-transform: scaleX(0);
  transform: scaleX(0);
  -webkit-transform-origin: 50%;
  transform-origin: 50%;
  -webkit-transition-property: transform;
  transition-property: transform;
  -webkit-transition-duration: 0.3s;
  transition-duration: 0.3s;
  -webkit-transition-timing-function: ease-out;
  transition-timing-function: ease-out;
}
.searchbar .btn-effect:hover,
.searchbar .btn-effect:focus,
.searchbar .btn-effect:active {
  color: white;
}
.searchbar .btn-effect:hover:before,
.searchbar .btn-effect:focus:before,
.searchbar .btn-effect:active:before {
  -webkit-transform: scaleX(1);
  transform: scaleX(1);
}

/* Removing the dotted line in firefox */
.searchbar button::-moz-focus-inner {
  border: 0;
}

.searchbar .input-wrapper {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

/* MEDIA QUERIES  */

@media screen and (max-width: 830px) {
  .searchbar .form-wrapper {
    margin: 0 auto;
  }
}
</style>
