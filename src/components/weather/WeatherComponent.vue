<template>
<div class="weather-wrapper" @click="openPopup = !openPopup">
  <div class="icon">
    <img :src="displayIcon()" alt="">
  </div>
  <div class="middle">
    <h2>{{data.data.main.temp}} °C</h2>
    <h5>{{data.data.name}}</h5>
  </div>
  <div style="position: absolute; top: 57%">
    <popup :data="data" v-if="openPopup"></popup>
  </div>
</div>
</template>

<script>
import Popup from "../utils/Popup";
export default {
  name: "WeatherComponent",
  components: {Popup},
  props: {
    data: {
      type: Object,
      default: null
    }
  },

  data(){
    return {
      openPopup: false
    }
  },

  methods: {
    displayIcon(){
      let condition = this.data.data.weather[0].description
      switch (condition){
        case 'clear sky':
          return process.env.VUE_APP_WEATHER_ICON_URL+'01d@2x.png'
        case 'few clouds':
          return process.env.VUE_APP_WEATHER_ICON_URL+'02d@2x.png'
        case 'scattered clouds':
          return process.env.VUE_APP_WEATHER_ICON_URL+'03d@2x.png'
        case 'broken clouds':
          return process.env.VUE_APP_WEATHER_ICON_URL+'04d@2x.png'
        case 'shower rain':
          return process.env.VUE_APP_WEATHER_ICON_URL+'09d@2x.png'
        case 'rain':
          return process.env.VUE_APP_WEATHER_ICON_URL+'10d@2x.png'
        case 'thunderstorm':
          return process.env.VUE_APP_WEATHER_ICON_URL+'11d@2x.png'
        case 'snow':
          return process.env.VUE_APP_WEATHER_ICON_URL+'13d@2x.png'
        case 'mist':
          return process.env.VUE_APP_WEATHER_ICON_URL+'50d@2x.png'
        default:
          return process.env.VUE_APP_WEATHER_ICON_URL+'01d@2x.png'
      }
    }
  }
}
</script>

<style scoped>
.middle{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
h4, h5, h2, h3{
  margin: 0.1rem;
}
.weather-wrapper{
  display: flex;
  justify-content: center;
}
.icon{
  margin: 0;
}
.icon:hover{
  cursor: pointer;
}
.middle:hover{
  cursor: pointer;
}
</style>