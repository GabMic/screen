<template>
  <div>
    <h1>{{time}}</h1>
    <h4>{{date}}</h4>
  </div>
</template>

<script>
export default {
  name: "DateComponent",
  props: {
    data: {
      type: Object,
      default: null
    }
  },

  data(){
    return {
      time: null,
     date: null,
    }
  },

  mounted() {
    setInterval(this.realTime, 1000)
    // const clock12 = document.getElementById('clock12')
    // const clock24 = document.getElementById('clock24')
  },
  methods: {
    realTime() {
      this.time = new Date().toLocaleTimeString()

      const options1 = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
      const dateTimeFormat2 = new Intl.DateTimeFormat('en-GB', options1);
      this.date = dateTimeFormat2.format(new Date());
      //let sec = date.getSeconds()
      // let mon = date.getMinutes()
      // let hr = date.getHours()
      // new Date().toLocaleTimeString()
      // // 12 hour time
      // // If the hour equals 0 or 12, the remainder equals 0, so output 12 instead. (0 || 12 = 12)
      // // `${this.concatZero((hr % 12) || 12)} : ${this.concatZero(mon)} : ${this.concatZero(sec)} ${hr >= 12 ? 'PM' : 'AM'}`
      // // 24 hour time
      //    `${this.concatZero(hr)} : ${this.concatZero(mon)} : ${this.concatZero(sec)}`
    },
    concatZero(timeFrame) {
      return timeFrame < 10 ? '0'.concat(timeFrame) : timeFrame
    }
  }
}
</script>

<style scoped>

</style>