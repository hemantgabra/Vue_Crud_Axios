<template>
  <div id="app">
    <ProductListing msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import ProductListing from "./components/ProductListing.vue";

export default {
  name: "App",
  components: {
    ProductListing
  }
};
</script>

<style>
@import "~bulma/css/bulma.css";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
