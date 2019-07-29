<template>
  <div id="app">
      <app-header></app-header>
      <app-books></app-books>
      <app-footer></app-footer>
  </div>
</template>

<script>
import Header from "./components/Header";
import Books from "./components/Books";
import Footer from "./components/Footer";

export default {
  name: "app",
  components: {
      "app-header": Header,
      "app-books": Books,
      "app-footer": Footer
  }
}
</script>

<style lang="css">
/* Global Styles */

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
  font-family: 'Montserrat', sans-serif;
  letter-spacing: .75px;
}

</style>