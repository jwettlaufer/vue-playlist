<template>
  <section>
    <h2>VUE PLAYLIST</h2>
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
      <ul class="song-list">
        <Song
          v-for="song in songs"
          :key="song.title"
          :song="song"
          v-on:delete-song="removeSong"
          v-on:like-song="likeSong"
          :class="{'liked-song' : song.favorite}"
        />
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
      newArtist: "",
      songs: [
        {
          title: "You're Welcome",
          artist: "Dwayne Johnson",
          favorite: true
        },
        {
          title: "High Hopes",
          artist: "Panic! at the Disco",
          favorite: false
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
    likeSong(song) {
      const faveIndex = this.songs.indexOf(song);
      this.songs[faveIndex].favorite = !this.songs[faveIndex].favorite;
    },
    removeSong(song) {
      const songIndex = this.songs.indexOf(song);
      this.songs.splice(songIndex, 1);
    }
  }
};
</script>

<style>
  .liked-song {
    font-style: italic;
    font-weight: bold;
  }
</style>