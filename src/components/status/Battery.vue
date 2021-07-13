<template>
  <div class="remaining"><i :class="icon" style="margin-right: 2px;"></i>{{ remaining }}%</div>
</template>

<script>
export default {
  name: "Battery",

  data() {
    return {
      remaining: 100,
      icon: 'fas fa-battery-full'
    }
  },
  mounted() {
    setInterval(this.handleBattery, 30000)
  },
  methods: {
    handleBattery() {
      if(this.remaining >0){
        this.remaining -= 1;
      }
      if(this.remaining >= 51 && this.remaining <= 74){
        this.icon = 'fas fa-battery-three-quarters'
      }
      if(this.remaining >= 25 && this.remaining <= 50){
        this.icon = 'fas fa-battery-half'
      }
      if(this.remaining >= 0 && this.remaining <= 24){
        this.icon = 'fas fa-battery-quarter'
      }
      if(this.remaining === 0 ){
        this.icon = 'fas fa-battery-empty'
      }
    }
  }

}
</script>

<style scoped>
.remaining{
  font-size: 13px;
  margin: 0;
  padding: 0;
  color: white;

}
</style>