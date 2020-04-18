<template>
  <li>
    {{song.title}} by {{song.artist}}
    <button v-on:click="removeSong( song )">X</button>
  </li>
</template>

<script>
export default {
  name: "Song",
  props: ["song"],
  methods: {
        removeSong (song) {
            this.$emit('delete-song', song);
        }
    }
};
</script>

<style>
li {
  text-align: left;
}
</style>