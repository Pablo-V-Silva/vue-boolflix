<template>
  <main>
    <div class="card" v-for="film in films" :key="film.id">
      <div class="filmThumb">
        <img
          :src="`https://image.tmdb.org/t/p/w500` + film.poster_path"
          alt=""
        />
      </div>
      <div class="infoFilm">
        <h2 class="title">{{ film.title }}</h2>
        <h3 class="originalName">{{ film.original_title }}</h3>
        <div style="font-size: 50px" v-if="film.original_language == 'en'">
          <flag iso="gb" />
        </div>
        <div style="font-size: 50px" v-else>
          <flag :iso="film.original_language" />
        </div>
        <p class="vote">{{ film.vote_average }}</p>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  props: {
    films: Array,
  },

  data() {
    return {};
  },

  mounted() {},

  methods: {},
};
</script>

<style>
</style>