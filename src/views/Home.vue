<template>
  <div>
    <MusicControler />
    <MusicLibrary />
  </div>
</template>
<script>
import MusicControler from "@/components/MusicControler.vue";
import MusicLibrary from "@/components/MusicLibrary.vue";

export default {
  name: "home",
  components: {
    MusicControler,
    MusicLibrary
  }
};
</script>
