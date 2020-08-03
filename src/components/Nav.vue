<template>
  <section id="Nav-container">
    <section id="Nav-section">
      <h3>Nav:</h3>
      <nav>
        <router-link to="/">Home</router-link>
      </nav>
    </section>
  </section>
</template>


<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  name: "Nav"
});
</script>

<style lang="scss" scoped>
#Nav-container {
  display: flex;
  flex-direction: row;
  background: $COLOR-BG-1;
  padding: 4px 10px;
  color: white;
  width: 100vw;

  #Nav-section {
    min-width: 20%;
    max-width: 800px;
    margin: 0 50px;
    margin-left: auto;

    &,
    h3,
    nav {
      @include flex-center-self;
    }

    nav {
      padding: 4px;
      margin-left: auto;
    }
  }
}
</style>
