<template>
  <div class="status-wrapper">
    <h5>T-Mobile</h5>
    <battery></battery>
  </div>
</template>

<script>
import Battery from "./Battery";
export default {
  name: "DeviceStatusContainer",
  components: {Battery}
}
</script>

<style scoped>
.status-wrapper{
  display: flex;
  justify-content: space-between;
  padding: 0 0.1rem 0 0.1rem;
  align-items: center;
}
h5{
  padding: 0;
  margin: 0;
}
</style>