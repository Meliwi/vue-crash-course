<template>
  <div id="app">
    <FiltersCreation />
    <ComputedProperties />
  </div>
</template>

<script>
import FiltersCreation from "./components/FiltersCreation.vue";
import ComputedProperties from "./components/ComputedProperties.vue";
export default {
  name: "App",
  components: {
    FiltersCreation,
    ComputedProperties,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
