<template>
  <div id="app" class="b-container-lg mx-auto my-4 bg-info">
    <b-container>
      <b-row>
        <b-col cols="6" offset="3">
          <!-- Controls -->
          <b-card class="mt-4">
            <b-row class="justify-content-between mx-2">
              <b-form-checkbox switch size="lg">Large</b-form-checkbox>
              <div class="border px-4 py-2">{{ currentSound }}</div>
            </b-row>
            <b-row class="mx-4 my-2">
              <label for="volume">Volume</label>
              <b-form-input id="volume" v-model="volume" type="range" min="0" max="10"></b-form-input>
            </b-row>
          </b-card>
          <!-- Drum buttons -->
          <b-card class="my-4">
            <b-row class="justify-content-center">
              <v-btn
                class="m-4 sound-button"
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
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<style>
.sound-button {
  width: 150px;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
.sound-button {
  cursor: pointer;
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
      volume: 0,
    };
  },
  created: function () {},
  mounted: function () {
    window.addEventListener("keydown", this._keyListener);
  },
  methods: {
    playSound: function (instrument) {
      // console.log(instrument);
      let instr = new Audio(instrument.src);
      this.currentSound = instrument.name;
      instr.play();
    },
    _keyListener: function (e) {
      // console.log(e);
      let key = e.key.toUpperCase();
      let param = this.sounds[key];
      // console.log(param);
      this.playSound(param);
    },
  },
};
</script>
