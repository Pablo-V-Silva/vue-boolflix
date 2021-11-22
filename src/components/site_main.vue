<template>
  <main>
    <div class="contain">
      <h2 class="my-4">Films :</h2>
      <div class="films row row-cols-5 g-4">
        <div class="col" v-for="film in films" :key="film.poster_path">
          <div class="card filmCard filmThumb text-center border-0 h-100">
            <div class="thumb h-100">
              <div class="h-100" v-if="film.poster_path === null">
                <div class="nothumb w-100 h-100 rounded"></div>
              </div>
              <img
                :src="`https://image.tmdb.org/t/p/w300` + film.poster_path"
                alt=""
                width="100%"
                height="100%"
                class="rounded thumb_no_hover"
                v-else
              />
            </div>
            <div
              class="
                infoFilm
                w-100
                px-3
                h-100
                d-flex
                flex-column
                justify-content-center
              "
            >
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
                    :key="star.qualunquecosa"
                    class="fas fa-star text-warning"
                  ></i>
                  <i
                    v-for="star in 5 - Math.round(film.vote_average / 2)"
                    :key="star.qualunquecosa"
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
      <h2 class="my-4">Series :</h2>
      <div class="films row row-cols-5 g-4">
        <div class="col" v-for="serie in series" :key="serie.poster_path">
          <div class="card filmCard filmThumb text-center border-0 h-100">
            <div class="thumb h-100">
              <div class="h-100" v-if="serie.poster_path === null">
                <div class="nothumb w-100 h-100 rounded"></div>
              </div>
              <img
                :src="`https://image.tmdb.org/t/p/w300` + serie.poster_path"
                alt=""
                width="100%"
                height="100%"
                class="rounded thumb_no_hover"
                v-else
              />
            </div>
            <div
              class="
                infoFilm
                w-100
                px-3
                h-100
                d-flex
                flex-column
                justify-content-center
              "
            >
              <div class="filmTitle w-100">
                <h3 class="title">{{ serie.name }}</h3>
                <h4 class="originalName">{{ serie.original_name }}</h4>
              </div>
              <div class="language d-flex justify-content-center">
                <p class="me-2">Language : {{ serie.original_language }}</p>
                <div v-if="serie.original_language == 'en'">
                  <flag iso="gb" />
                </div>
                <div v-else-if="serie.original_language == 'it'">
                  <flag iso="it" />
                </div>
                <div v-else-if="serie.original_language == 'ja'">
                  <flag iso="jp" />
                </div>
                <div v-else-if="serie.original_language == 'zh'">
                  <flag iso="cn" />
                </div>
                <div v-else>
                  <flag :iso="serie.original_language" />
                </div>
              </div>

              <div class="vote">
                <div class="vote">
                  <i
                    v-for="star in Math.round(serie.vote_average / 2)"
                    :key="star.qualunquecosa"
                    class="fas fa-star text-warning"
                  ></i>
                  <i
                    v-for="star in 5 - Math.round(serie.vote_average / 2)"
                    :key="star.qualunquecosa"
                    class="far fa-star"
                  ></i>
                </div>
              </div>

              <div class="plot" v-if="serie.overview != ''">
                <p v-if="serie.overview.length > 200">
                  Plot: {{ serie.overview.substring(-1, 200) + "..." }}
                </p>
                <p v-else>Plot: {{ serie.overview }}</p>
              </div>
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

    &:hover {
      transform: scale(1.1);
      -webkit-box-shadow: 1px 4px 40px 11px #2b0000;
      -moz-box-shadow: 1px 4px 40px 11px #2b0000;
      -o-box-shadow: 1px 4px 40px 11px #2b0000;
      box-shadow: 1px 4px 40px 11px #2b0000;
      z-index: 100;
    }

    &:hover img {
      border-radius: 6px;
    }

    &:hover .infoFilm {
      visibility: visible;
      background-color: rgba(77, 77, 77, 0.55);
    }

    .nothumb {
      background-image: url("https://www.publicdomainpictures.net/pictures/280000/velka/not-found-image-15383864787lu.jpg");
      background-size: cover;
      background-repeat: no-repeat;
      background-position: center;
    }

    .infoFilm {
      position: absolute;
      visibility: hidden;

      h2.title {
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
    }
  }
}
</style>