<template>
  <footer>
    <section id="contact">
      <h2>Contact me on email</h2>
      <a :href="`mailto:${email}`">Email: post@kjetil.codes</a>
      <button @click="copyEmail()" title="Doesn't work in Firefox">Copy</button>
    </section>
  </footer>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  name: "Footer",
  data() {
    return {
      email: "post@kjetil.codes"
    };
  },
  methods: {
    copyEmail() {
      console.log(this.email);
      navigator.clipboard
        .writeText(this.email)
        .then(e => e)
        .catch(e => e);
    }
  }
});
</script>

<style lang="scss" scoped>
button {
  border: none;
  background: none;
  color: #ffcc00;
  text-decoration: underline;
  border: 1px #ffcc00 solid;
  font-size: 0.8rem;
  border-radius: 5px;
  margin: 10px;
}
footer {
  display: flex;
  align-items: center;
  justify-content: center;
  background: black;
  padding: 10px;
  margin-top: auto;
  color: #cccccc;
}
</style>
