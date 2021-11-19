<template>
  <main>
    <div class="films">
      <h2>Films :</h2>
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
          <div
            style="font-size: 50px"
            v-else-if="film.original_language == 'it'"
          >
            <flag iso="it" />
          </div>
          <div
            style="font-size: 50px"
            v-else-if="film.original_language == 'ja'"
          >
            <flag iso="jp" />
          </div>
          <div
            style="font-size: 50px"
            v-else-if="film.original_language == 'zh'"
          >
            <flag iso="cn" />
          </div>
          <div v-else>
            <p>{{ film.original_language }}</p>
          </div>
          <div class="vote">
            <span
              class="vote"
              v-for="star in Math.round(film.vote_average / 2)"
              :key="star"
            >
              <i class="fas fa-star"></i>
            </span>
            <span
              class="vote"
              v-for="star in 5 - Math.round(film.vote_average / 2)"
              :key="star"
            >
              <i class="far fa-star"></i>
            </span>
          </div>
        </div>
      </div>
    </div>

    <div class="series">
      <h2>Series :</h2>
      <div class="card" v-for="serie in series" :key="serie.id">
        <div class="serieThumb">
          <img :src="`https://image.tmdb.org/t/p` + serie.poster_path" alt="" />
        </div>
        <div class="infoFilm">
          <h2 class="title">{{ serie.name }}</h2>
          <h3 class="originalName">{{ serie.original_name }}</h3>
          <div style="font-size: 50px" v-if="serie.original_language == 'en'">
            <flag iso="gb" />
          </div>
          <div
            style="font-size: 50px"
            v-else-if="serie.original_language == 'it'"
          >
            <flag iso="it" />
          </div>
          <div
            style="font-size: 50px"
            v-else-if="serie.original_language == 'ja'"
          >
            <flag iso="jp" />
          </div>
          <div
            style="font-size: 50px"
            v-else-if="serie.original_language == 'zh'"
          >
            <flag iso="cn" />
          </div>
          <div style="font-size: 50px" v-else>
            <p>{{ serie.original_language }}</p>
          </div>
          <div class="vote">
            <span
              class="vote"
              v-for="star in Math.round(serie.vote_average / 2)"
              :key="star"
            >
              <i class="fas fa-star"></i>
            </span>
            <span
              class="vote"
              v-for="star in 5 - Math.round(serie.vote_average / 2)"
              :key="star"
            >
              <i class="far fa-star"></i>
            </span>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  props: {
    films: Array,
    series: Array,
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