<template>
  <li class="song-item">
    {{song.title}} by {{song.artist}}
    <button class="unliked-button" v-if="!song.favorite" @click="likeSong( song )">♥</button>
    <button class="liked-button" v-else @click="likeSong( song )">♥</button>
    <button v-on:click="removeSong( song )">X</button>
  </li>
</template>

<script>
export default {
  name: "Song",
  props: ["song"],
  methods: {
    likeSong(song) {
      this.$emit("like-song", song);
    },
    removeSong(song) {
      this.$emit("delete-song", song);
    }
  }
};
</script>

<style>
.liked-button {
 color: red;
}
</style>