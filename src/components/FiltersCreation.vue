<template>
  <div id="card">
    <header>{{ title | capitalize }}</header>
    <ul>
      <li v-for="(dino, index) in dinos" :key="index">
        <h4>{{ dino.text | capitalize }}</h4>
        <span>The {{ dino.text }} weighs {{ dino.weight }}</span>
        <br />
        <a href="">{{ dino.text | undercase | url }}</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "FiltersCreation",
  data() {
    return {
      title: "Dinosaurs",
      dinos: [
        { text: "Velociraptor", weight: "15 kg" },
        { text: "Triceratops", weight: "6,000 kg" },
        { text: "Stegosaurus", weight: "2,500 kg" },
      ],
    };
  },
  filters: {
    capitalize: function (value) {
      if (!value) return "";
      value = value.toString();
      return value.charAt(0).toUpperCase() + value.slice(1);
    },
    undercase: function (value) {
      if (!value) return "";
      value = value.toString();
      return value.toLowerCase();
    },
    url: function (value) {
      if (!value) return "";
      value = value.toString();
      return "https://en.wikipedia.org/wiki/" + value;
    },
  },
};
</script>

<style>
@import "../css/styles.css";
</style>
