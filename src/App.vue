<template>
  <div id="app">
    <SiteHeader @search-film="searchFilms" />
    <SiteMain :films="filmsArray" />
    <SiteFooter />
  </div>
</template>

<script>
import SiteHeader from "./components/site_header.vue";
import SiteMain from "./components/site_main.vue";
import SiteFooter from "./components/site_footer.vue";

import axios from "axios";

export default {
  name: "App",
  components: {
    SiteHeader,
    SiteMain,
    SiteFooter,
  },

  data() {
    return {
      selectString: "",
      filmsArray: [],
    };
  },

  methods: {
    searchFilms(string) {
      this.selectString = string;
      console.log(this.selectString);
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=cf5485ae1b12cfa22015f6beb6f48410&query=${string}`
        )
        .then((resp) => {
          this.filmsArray = resp.data.results;
          console.log(this.filmsArray);
        });
    },
  },
};
</script>

<style lang="scss">
</style>
