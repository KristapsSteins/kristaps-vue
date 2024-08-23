<template>
  <MainComponent />
</template>

<script>
import MainComponent from "./components/MainComponent.vue";

export default {
  name: "App",
  components: {
    MainComponent,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  padding: 60px 20px 0 20px;
  max-width: 800px;
  margin: auto;
  background-image: url("@/assets/background.jpg");
  background-size: cover;
  height: 100vh;
  color: #010101;
}
</style>
