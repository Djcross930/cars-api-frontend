<script>
import axios from "axios"
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      cars: [],
      currentCar: {}
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
    },
    showCar: function (theCar) {
      console.log(theCar)
      this.currentCar = theCar
      document.querySelector('#car-details').showModal()
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
      <button v-on:click="showCar(car)">More Info</button>
      <br />
      <br />
    </div>
    <dialog id="car-details">
      <form method="dialog">
        <p><b>make:</b> {{ currentCar.make }}</p>
        <p><b>year:</b> {{ currentCar.year }}</p>
        <p><b>color:</b> {{ currentCar.color }}</p>
      </form>
    </dialog>
  </div>
</template>

<style>
</style>