<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1 class="title">Calculator App</h1>
    <Calculator />
  </div>
</template>

<script>
import Calculator from "./components/Calculator.vue";

export default {
  name: "App",
  components: {
    Calculator
  }
};
</script>

<style>
@import "App.css";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  position: relative;
  min-height: 100vh;
  overflow: hidden;
}

img {
  position: absolute;
  top: 3rem;
  left: 3rem;
  height: 3rem;
}

.title {
  font-size: 5rem;
  text-align: center;
  margin-top: 2rem;
  background-image: linear-gradient(#51ffb1, #6ba0d4);
  background-clip: text;
  color: transparent;
}
</style>
