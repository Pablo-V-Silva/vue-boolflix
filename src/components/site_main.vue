<template>
  <main>
    <div class="card" v-for="film in films" :key="film.id">
      <div class="filmThumb">
        <img src="" alt="" />
      </div>
      <div class="infoFilm">
        <h2 class="title">{{ film.title }}</h2>
        <h3 class="originalName">{{ film.original_title }}</h3>
        <p class="language">{{ film.original_language }}</p>
        <p class="vote">{{ film.vote_average }}</p>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      films: [],
    };
  },

  mounted() {},

  methods: {
    searchFilms() {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=cf5485ae1b12cfa22015f6beb6f48410&language=it-IT&query=n&page=1&include_adult=false"
        )
        .then((resp) => {
          this.films = resp.data.results;
        });
    },
  },
};
</script>

<style>
</style>