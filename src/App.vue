<template>
  <div id="app">
    <device-status-container></device-status-container>

    <div class="center-screen">
      <date-component></date-component>
      <weather-component></weather-component>
    </div>

    <news-component></news-component>
  </div>
</template>

<script>
import DeviceStatusContainer from "./components/status/DeviceStatusContainer";
import WeatherComponent from "./components/weather/WeatherComponent";
import DateComponent from "./components/date/DateComponent";
import NewsComponent from "./components/news/NewsComponent";
import axios from "axios"
export default {
  name: 'App',
  components: {
    NewsComponent,
    DateComponent,
    WeatherComponent,
    DeviceStatusContainer
  },
  data(){
    return{
      weather: null,
      date: null
    }
  },
  methods:{
    fetchData(){
      //axios.get()
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
