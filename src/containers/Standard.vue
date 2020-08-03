<template>
  <section class="standard-container">
    <Header />
    <slot></slot>
    <Footer />
  </section>
</template>

<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
export default {
  name: "Standard",
  components: { Header, Footer }
};
</script>

<style lang="scss" scoped>
@media (min-width: 500px) {
  article {
    min-width: 100%;
  }

  .standard-container {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    min-width: 100%;
  }
  section,
  div,
  .container {
    display: flex;
    flex-direction: column;
    grid-template: auto(1fr, 10) / auto(1fr, 100);
  }

  article {
    max-width: 30vw;
    color: $FONT-1;
    margin: 10px;
  }

  li {
    list-style-type: none;
  }
}
</style>
