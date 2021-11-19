<template>
  <main>
    <div class="card" v-for="film in films" :key="film.id">
      <div class="filmThumb">
        <img
          :src="`https://image.tmdb.org/t/p/w500` + film.poster_path"
          alt=""
          width="100px"
        />
      </div>
      <div class="infoFilm">
        <h2 class="title">{{ film.title }}</h2>
        <h3 class="originalName">{{ film.original_title }}</h3>
        <div style="font-size: 50px" v-if="film.original_language == 'en'">
          <flag iso="gb" />
        </div>
        <div style="font-size: 50px" v-else-if="film.original_language == 'it'">
          <flag iso="it" />
        </div>
        <div style="font-size: 50px" v-else-if="film.original_language == 'ja'">
          <flag iso="jp" />
        </div>
        <div style="font-size: 50px" v-else-if="film.original_language == 'zh'">
          <flag iso="cn" />
        </div>
        <div style="font-size: 50px" v-else>
          {{ film.original_language }}
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