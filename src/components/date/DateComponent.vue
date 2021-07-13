<template>
  <div>
    <h1 v-if="time">{{time}}</h1>
    <h1 v-if="time === null">Loading...</h1>
    <h4>{{date}}</h4>
  </div>
</template>

<script>
export default {
  name: "DateComponent",
  data(){
    return {
      time: null,
      date: null,
    }
  },

  mounted() {
    setInterval(this.realTime, 1000)
  },
  methods: {
    realTime() {
      this.time = new Date().toLocaleTimeString()
      const options1 = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
      const dateTimeFormat2 = new Intl.DateTimeFormat('en-GB', options1);
      this.date = dateTimeFormat2.format(new Date());
    },
  }
}
</script>

<style scoped>

</style>