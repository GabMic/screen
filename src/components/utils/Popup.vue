<template>
<div class="popup-wrapper">
  <div style="display: flex; flex-direction: column; justify-content: space-between; margin: 2px">
    <h6>Wind Speed</h6>
    <h5>{{ data.data.wind.speed }}</h5>
  </div>
  <div style="display: flex; flex-direction: column; justify-content: center; margin: 2px">
     <h6>Feels Like</h6>
    <h5>{{data.data.main.feels_like}} °C</h5>
  </div>
  <div style="display: flex; flex-direction: column; justify-content: center; margin: 2px">
    <h6>Condition</h6>
    <h5>{{ data.data.weather[0].description }}</h5>
  </div>
</div>
</template>

<script>
export default {
  name: "Popup",
  props: {
    data: {
      type: Object
    }
  }
}
</script>

<style scoped>
.popup-wrapper{
  display: flex;
  width: 200px;
  height: 100px;
  border-radius: 5px;
  border: 2px solid white;
  justify-content: space-around;
  align-items: center;
  box-shadow: 0 3px 10px rgb(0 0 0 / 0.2);
}
h6, h5{
  margin: 0;
  padding: 0;
}
h5{
  font-size: 10px;
}
</style>