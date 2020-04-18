<template>
  <section>
    <h2>Vue Playlist</h2>
    <h3>Add a New Song:</h3>
    <form @submit="addSong">
      <label for="new-song">
        Title:
        <input type="text" name="title" v-model="newSong" />
        Artist:
        <input type="text" name="artist" v-model="newArtist" />
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
          title: "You're Welcome",
          artist: 'Dwayne Johnson'
        }
      ]
    };
  },
  methods: {
    addSong(event) {
      event.preventDefault();
      const newSong = this.newSong;
      const newArtist = this.newArtist;
      this.songs.push({
        title: newSong,
        artist: newArtist
      });
      this.newSong = ""; 
      this.newArtist = "";
    }
  }
};
</script>

<style>
</style>