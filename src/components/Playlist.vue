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
    <div class="like-song">
    <ul>
      <Song v-for="song in songs" :key="song.title" :song="song" v-on:delete-song="removeSong"/>
    </ul>
    </div>
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
      newArtist: "",
      songs: [
        {
          title: "You're Welcome",
          artist: 'Dwayne Johnson',
          favorite: true 
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
        artist: newArtist,
        favorite: false
      });
      this.newSong = ""; 
      this.newArtist = "";
    },
    removeSong(song) {
      const songIndex = this.songs.indexOf(song);
      this.songs.splice(songIndex, 1);
    }
  }
};
</script>

<style>

</style>