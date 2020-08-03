<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Header from "@/components/Header.vue";
import Nav from "@/components/Nav.vue";
import Footer from "@/components/Footer.vue";

export default Vue.extend({
  name: "App"
});
</script>

<style lang="scss">
@import "../node_modules/normalize.css/normalize.css";
a {
  text-decoration: none;
  text-decoration: underline;
  color: inherit;
  color: cyan;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  min-height: 110vh;
}

.container {
  padding: 20px 50px;
}
</style>
