<template>
  <div id="app" class="b-container-lg mx-auto my-4 bg-info">
    <b-container>
      <b-row>
        <b-col cols="6" offset="3">
          <!-- Controls -->
          <b-card class="mt-4">
            <b-row class="justify-content-between mx-2">
              <b-form-checkbox switch size="lg">Large</b-form-checkbox>
              <div class="border px-4 py-2">Sound Name</div>
            </b-row>
            <b-row class="mx-4 my-2">
              <label for="volume">Volume</label>
              <b-form-input id="volume" v-model="volume" type="range" min="0" max="10"></b-form-input>
            </b-row>
          </b-card>
          <!-- Drum buttons -->
          <b-card class="mt-4">
            <b-row class="justify-content-center">
              <div class="sound-button bg-info">X</div>
            </b-row>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<style scoped>
.sound-button {
  width: 200px;
  height: 200px;
}
</style>

<script>
// import axios from "axios";
import audio from "./audio";
let snare = new Audio("/audio/snare.wav");
export default {
  name: "App",
  components: {},
  data: function () {
    return {
      audio,
    };
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
