<script>
import axios from "axios"
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      cars: []
    };
  },
  created: function () {
    this.indexCars()
  },
  methods: {
    indexCars: function () {
      axios.get("/cars").then((response) => {
        console.log(response.data)
        this.cars = response.data
      })
    }
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="car in cars">
      <p>{{ car.make }}</p>
      <p> {{ car.year }} </p>
      <p> {{ car.color }} </p>
      <br />
      <br />
    </div>
  </div>
</template>

<style>
</style>