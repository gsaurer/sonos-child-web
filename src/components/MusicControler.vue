<template>
  <div class="control">
    <div class="control-panel">
      <img src="../assets/play.png" alt="Play" @click.self="play" />
      <img src="../assets/stop.png" alt="Stop" @click.self="stop" />
    </div>
    <div class="control-panel">
      <img src="../assets/previous.png" alt="Previous" @click.self="prevTrack" />
      <img src="../assets/next.png" alt="Next" @click.self="nextTrack" />
    </div>
    <div class="control-panel">
      <img src="../assets/volume_up.png" alt="Volume Up" @click.self="volumeUp" />
      <img src="../assets/volume_down.png" alt="Volume down" @click.self="volumeDown" />
    </div>
  </div>
</template>


<script>
import config from "@/config/config.json";
import axios from "axios";

export default {
  name: "MusicController",
  data() {
    return {};
  },
  methods: {
    play() {
      var url = config.url + config.room + "/play";
      axios.get(url).then(results => {
        this.results = results.data;
        //alert(results.data);
      });
    },
    stop() {
      var url = config.url + config.room + "/stop";
      axios.get(url).then(results => {
        this.results = results.data;
        //alert(results.data);
      });
    },
    prevTrack() {
      var url = config.url + config.room + "/previous";
      axios.get(url).then(results => {
        this.results = results.data;
        //alert(results.data);
      });
    },
    nextTrack() {
      var url = config.url + config.room + "/next";
      axios.get(url).then(results => {
        this.results = results.data;
        //alert(results.data);
      });
    },
    volumeUp() {
      var url = config.url + config.room + "/volume/+2";
      axios.get(url).then(results => {
        this.results = results.data;
        //alert(results.data);
      });
    },
    volumeDown() {
      var url = config.url + config.room + "/volume/-2";
      axios.get(url).then(results => {
        this.results = results.data;
        //alert(results.data);
      });
    }
  }
};
</script>

<style>
.control {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(20rem, 1fr));
  grid-gap: 1rem;
  max-width: 80rem;
  margin: 5rem auto;
  padding: 0 5rem;
}
.control-panel img {
  width: 60px;
  height: 60px;
  object-fit: cover;
  padding: 5px;
}
</style>