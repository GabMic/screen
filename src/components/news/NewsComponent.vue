<template>

  <div class="ticker-wrap">
    <div class="ticker">
      <div class="ticker_item"><a v-for="(news, i) in data" :href="news.url" :key="i" style="margin-left: 5px;
    margin-right: 5px; color: white; text-decoration: none">{{news.title}}</a></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NewsComponent",
  props: {
    data: {
      type: Object
    }
  }
}
</script>

<style scoped>
@-webkit-keyframes ticker {
  0% {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    visibility: visible;
  }
  100% {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
  }
}
@keyframes ticker {
  0% {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    visibility: visible;
  }
  100% {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
  }
}
.ticker-wrap {
  width: 100%;
  overflow: hidden;
  height: 3rem;
  background-color: inherit;
  border-top: 1px solid white;
}

.ticker {
  display: inline-block;
  height: 3rem;
  line-height: 3rem;
  white-space: nowrap;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  animation-name: ticker;
  animation-duration: 240s;
}
.ticker_item {
  display: inline-block;
  padding: 0 2rem;
  font-size: 1rem;
  color: white;
}

</style>