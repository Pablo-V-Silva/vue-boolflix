<template>
  <main>
    <div class="contain">
      <h2>Films :</h2>
      <div class="films row row-cols-5 g-3">
        <div class="col" v-for="film in films" :key="film.poster_path">
          <div
            class="
              card
              filmCard
              filmThumb
              text-center
              position-relative
              border-0
              h-100
            "
          >
            <div class="thumb h-100">
              <div class="h-100" v-if="film.poster_path === null">
                <div class="nothumb w-100 h-100 rounded"></div>
              </div>
              <img
                :src="`https://image.tmdb.org/t/p/w300` + film.poster_path"
                alt=""
                width="100%"
                height="100%"
                class="rounded"
                v-else
              />
            </div>
            <div class="infoFilm w-100 px-3">
              <div class="filmTitle w-100">
                <h3 class="title">{{ film.title }}</h3>
                <h4 class="originalName">{{ film.original_title }}</h4>
              </div>
              <div class="language d-flex justify-content-center">
                <p class="me-2">Language : {{ film.original_language }}</p>
                <div v-if="film.original_language == 'en'">
                  <flag iso="gb" />
                </div>
                <div v-else-if="film.original_language == 'it'">
                  <flag iso="it" />
                </div>
                <div v-else-if="film.original_language == 'ja'">
                  <flag iso="jp" />
                </div>
                <div v-else-if="film.original_language == 'zh'">
                  <flag iso="cn" />
                </div>
                <div v-else>
                  <flag :iso="film.original_language" />
                </div>
              </div>

              <div class="vote">
                <div class="vote">
                  <i
                    v-for="star in Math.round(film.vote_average / 2)"
                    :key="star"
                    class="fas fa-star text-warning"
                  ></i>
                  <i
                    v-for="star in 5 - Math.round(film.vote_average / 2)"
                    :key="star"
                    class="far fa-star"
                  ></i>
                </div>
              </div>

              <div class="plot" v-if="film.overview != ''">
                <p>Plot: {{ film.overview.substring(-1, 100) + "..." }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="contain">
      <div class="series">
        <h2>Series :</h2>
        <div class="card" v-for="serie in series" :key="serie.poster_path">
          <div class="serieThumb">
            <img
              :src="`https://image.tmdb.org/t/p/w300${serie.poster_path}`"
              alt=""
            />
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

<style lang="scss">
@import "../assets/scss/variables.scss";

main {
  background-color: $main_color;
  color: $text_color;
  height: calc(100vh - 120px);
  overflow-y: auto;

  .filmCard {
    min-height: 440px;

    .nothumb {
      background-image: url("https://www.publicdomainpictures.net/pictures/280000/velka/not-found-image-15383864787lu.jpg");
      background-size: cover;
      background-repeat: no-repeat;
      background-position: center;
    }

    .infoFilm {
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);

      h2.title {
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
    }
  }
}
</style>