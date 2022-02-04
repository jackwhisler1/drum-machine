<template>
  <div class="container-lg mx-auto my-4 bg-info">
    <div class="container-md">
      <h1 class="display-1 text-center">Drum Machine</h1>
      <div class="row">
        <div class="col bg-primary">1 of 3</div>
        <div class="col-6 bg-white">2 of 3 (wider)</div>
        <div class="col bg-primary">3 of 3</div>
      </div>
      <div class="row p-2">
        <div class="col bg-primary">
          <button v-on:click="playSound()" class="btn btn-block btn-danger">Click me</button>
        </div>
        <div class="col-5 bg-white">2 of 3 (wider)</div>
        <div class="col bg-primary">3 of 3</div>
      </div>
    </div>
  </div>
</template>

<script>
// import axios from "axios";
let snare = new Audio("/audio/snare.wav");
export default {
  data: function () {
    return {};
  },
  created: function () {},
  mounted: function () {},
  methods: {
    playSound: function () {
      snare.play();
      console.log("snare!");
    },
  },
};
</script>
