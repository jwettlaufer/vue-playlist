<template>
  <section>
    <h2>Vue Playlist</h2>
    <h3>Add a New Song:</h3>
    <form @submit="addSong">
      <label for="new-song">
        Song Title:
        <input type="text" name="song" v-model="newSong" />
        Artist:
        <input type="text" name="artist" v-model="newSong" />
      </label>
      <input type="submit" value="Submit" />
    </form>
    <ul>
      <Song v-for="song in songs" :key="song.title" :song="song" />
    </ul>
  </section>
</template>

<script>
import Song from "./Song.vue";
export default {
  name: "Playlist",
  components: {
    Song
  },
  data() {
    return {
      newSong: "",
      songs: [
        {
          title: "You're Welcome"
        }
      ]
    };
  },
  methods: {
    addSong(event) {
      event.preventDefault();
      const newSong = this.newSong;
      this.songs.push({
        title: newSong
      });
      this.newSong = ""; //Clear the value after adding, so it is easy for the user to add more.
    }
  }
};
</script>

<style>
</style>