<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="place in places">
    {{ place.name }}
    <hr>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Places!",
      places: [],
    };
  },
  created: function () {
    console.log("in created");
    this.placesIndex();
  },
  methods: {
    placesIndex: function () {
      console.log("in places index");
      // get data from the api, then show data to user
      axios.get("http://localhost:3000/api/places").then((response) => {
        console.log(response.data);
        this.places = response.data;
      });
    },
  },
};
</script>

