<template>
  <CardBackground />
</template>

<script>
import CardBackground from "./components/CardBackground.vue";
export default {
  name: "App",
  components: {
    CardBackground,
  },
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  font-family: "Poppins", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
