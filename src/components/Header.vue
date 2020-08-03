<template>
  <header id="main-header">
    <h1>Kjetil.Codes</h1>
  </header>
</template>

<style lang="scss" scoped>
header {
  display: grid;
  grid-template-columns: repeat(10, 1fr);
  grid-template-rows: repeat(10, 1fr);
  min-height: 20vh;
  max-height: 20vh;
  background: linear-gradient(
      to bottom right,
      COLOR-primary-transp(dd) 50%,
      COLOR-primary-transp(aa)
    ),
    url("../assets/bg.jpg");
  h1 {
    font-size: 10vh;
    text-shadow: 0 0 1px #000;
    grid-column-start: 2;
    color: #fff;
    transform: translateY(4vh);
  }
}
</style>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  name: "Header"
});
</script>
