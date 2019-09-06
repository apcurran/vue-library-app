<template>
  <div id="app" class="container">
      <app-header></app-header>
      <app-books class="app-books"></app-books>
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

html,
button {
  font-family: 'Montserrat', sans-serif;
  letter-spacing: .04em;
}

.container {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}

.app-books {
  flex: 1;
}

</style>