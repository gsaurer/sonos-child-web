<template>
  <div>
    <div class="gallery">
      <div class="gallery-panel" v-for="music in musiclibrary" :key="music.id">
        <img :src="thumbUrl(music.filename)" :alt="music.uri" @click.self="play(music.uri)" />
      </div>
    </div>
  </div>
</template>

<script>
import musiclibrary from "@/data/musiclibrary.json";
import config from "@/config/config.json";
import axios from 'axios';

export default {
  name: "Gallery",
  data() {
    return {
      musiclibrary
    };
  },
  methods: {
    thumbUrl(filename) {
      return require(`../data/images/${filename}`);
    },
    play(uri) {
      var url = config.url + config.room + "/nfc/" + uri;
      axios
        .get(url)
        .then(results => {
          this.results = results.data;
          alert(results.data);
        });
    }
  }
};
</script>

<style>
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(20rem, 1fr));
  grid-gap: 1rem;
  max-width: 80rem;
  margin: 5rem auto;
  padding: 0 5rem;
  align-items: center;
}
.gallery-panel img {
  width: 100%;
  object-fit: cover;
  border-radius: 0.75rem;
}
</style>