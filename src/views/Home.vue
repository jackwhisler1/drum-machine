<template>
  <div id="app" class="b-container-lg mx-auto my-4 bg-dark">
    <b-container>
      <b-row>
        <b-col cols="6" offset="3">
          <!-- Controls -->
          <b-card class="mt-4 drum-buttons">
            <b-row class="justify-content-between mx-2">
              <b-form-checkbox v-model="isOn" switch size="lg">Power</b-form-checkbox>
              <div class="border px-4 py-2">{{ currentSound }}</div>
            </b-row>
            <b-row class="mx-4 my-2">
              <label for="volume">Volume</label>
              <b-form-input
                id="volume"
                v-model="volume"
                type="range"
                min="0"
                max="10"
                class="custom-range"
              ></b-form-input>
            </b-row>
          </b-card>
          <!-- Drum buttons -->
          <div v-if="isOn">
            <b-card class="my-4 justify-content-center drum-buttons">
              <b-row class="justify-content-center">
                <v-btn
                  class="m-3 sound-button"
                  x-large
                  elevation="15"
                  color="green"
                  v-for="(sound, index) in sounds"
                  :key="sound.name"
                  @click="playSound(sound)"
                >
                  {{ sound.name }}
                  <br />
                  {{ index }}
                </v-btn>
              </b-row>
            </b-card>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<style>
.sound-button {
  width: 26%;
  height: 130px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  overflow: hidden;
}
.drum-buttons {
}
.custom-range::-webkit-slider-thumb {
  background: gray;
}

.custom-range::-moz-range-thumb {
  background: gray;
}

.custom-range::-ms-thumb {
  background: gray;
}
</style>

<script>
// import sound files
import sounds from "../audio/sounds";

export default {
  name: "App",
  components: {},
  data: function () {
    return {
      sounds,
      currentSound: "Drum",
      volume: 5,
      isOn: true,
    };
  },
  created: function () {},
  mounted: function () {
    window.addEventListener("keydown", this._keyListener);
  },
  methods: {
    playSound: function (instrument) {
      if (this.isOn === true) {
        let instr = new Audio(instrument.src);
        this.currentSound = instrument.name;
        instr.volume = this.volume / 10.0;
        instr.play();
      }
    },
    _keyListener: function (e) {
      let key = e.key.toUpperCase();
      let param = this.sounds[key];
      this.playSound(param);
    },
  },
};
</script>
