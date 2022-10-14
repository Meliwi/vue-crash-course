<template>
  <div id="card">
    <header>{{ title }}<span></span></header>
    <form v-on:submit.prevent="addItem">
      <input v-on:input="debounceInput" id="itemForm" v-model="input" />
      <button v-bind:disabled="buttonDisabled">{{ buttonText }}</button>
    </form>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <button v-on:click="item.quantity += 1">+</button> {{ item.quantity }}
        <button v-on:click="item.quantity -= 1">-</button> {{ item.text
        }}<button v-on:click="removeItem" class="extinct">Make Extinct</button>
      </li>
    </ul>
    <ul>
      <li>
        Total Dinosaurs: {{ totalDinos }}
        <span>Updated: {{ dinosUpdated }}</span>
      </li>
      <li>
        Total Species: {{ totalSpecies }}
        <span>Updated: {{ speciesUpdated }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ComputedProperties",
  data() {
    return {
      title: "Dinosaurs",
      input: "",
      speciesUpdated: 0,
      dinosUpdated: 0,
      buttonText: "Add Dinosaur",
      items: [
        { text: "Tyrannosaurus", quantity: 5 },
        { text: "Triceratops", quantity: 3 },
        { text: "Stegosaurus", quantity: 6 },
      ],
    };
  },
  computed: {
    totalDinos() {
      //this.dinosUpdated += 1;
      var sum = 0;
      var items = this.items;

      for (var i in items) {
        sum += items[i].quantity;
      }

      return sum;
    },
    totalSpecies() {
      //this.speciesUpdated += 1;
      return this.items.length;
    },
  },
  methods: {
    addItem: function (e) {
      e.preventDefault();
      if (!this.input) return;

      this.items.push({ text: this.input, quantity: 1 });
      this.input = "";
    },
    removeItem: function (item) {
      this.items.splice(item, 1);
    },
  },
};
</script>
