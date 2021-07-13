<template>
  <div id="app">
    <device-status-container></device-status-container>
    <div class="center-screen">
      <date-component></date-component>
      <weather-component :data="weather"></weather-component>
    </div>

    <news-component :data="news"></news-component>
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
      news: null,
    }
  },
  mounted(){
    this.fetchData()
  },
  methods:{
    fetchData(){
      try{
        axios.get(process.env.VUE_APP_WEATHER_API_URL+`jerusalem&units=metric&appid=${process.env.VUE_APP_WEATHER_API_KEY}`)
            .then(res => {
              this.weather = res
            })
      }catch (error){
        console.log(error)
      }

      try{
        axios.get(process.env.VUE_APP_NEWS_URL+`?apikey=${process.env.VUE_APP_NEWS_API_KEY}&q=tech&language=en`)
            .then(res => {
              this.news = res.data.articles
            })
      }catch (error){
        console.log(error)
      }
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
  height: 97vh;
  color: white;
  padding: 0.2rem;
  background: rgb(2,0,36);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(1,41,57,1) 4%, rgba(103,7,167,0.7287289915966386) 25%, rgba(233,26,26,1) 81%, rgba(195,61,111,1) 100%, rgba(0,212,255,1) 100%);
}

</style>
