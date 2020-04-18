<template>
  <li>{{song.title}} by {{song.artist}}</li>
</template>

<script>
export default {
  name: "Song",
  props: ["song"]
};
</script>

<style>
li {
  text-align: left;
}
</style>