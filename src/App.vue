<template>
  <div id="app">
    <HeaderNetflix @emitSearchTextHeader="searchMovies" />
    <MainNetflix
      :arrayResultApp="filmResults"
      :arraySeriesApp="seriesResults"
    />
  </div>
</template>

<script>
import HeaderNetflix from "./components/HeaderNetflix.vue";
import MainNetflix from "./components/MainNetflix.vue";
import axios from "axios";

export default {
  
  name: "App",
  components: {
    HeaderNetflix,
    MainNetflix,
  },

  data() {
    return {
      searchTextFromHeaderToApp: "",
      searchQueryUrl: "",
      searchQueryUrlSeries: "",

      filmResults: [],
      seriesResults: [],
    };
  },

  mounted() {
    
  },

  methods: {

    searchMovies(searchTextHeader) {
      this.searchTextFromHeaderToApp = searchTextHeader;

      this.searchQueryUrl =
        "https://api.themoviedb.org/3/search/movie?api_key=c71a65738820e4777aa2511a3d0fece4&language=en-US&page=1&include_adult=false&query=" +
        this.searchTextFromHeaderToApp;

      axios.get(this.searchQueryUrl).then((response) => {
        this.filmResults = response.data.results;
      });

      this.searchQueryUrlSeries =
        "https://api.themoviedb.org/3/search/tv?api_key=c71a65738820e4777aa2511a3d0fece4&language=en-US&page=1&include_adult=false&query=" +
        this.searchTextFromHeaderToApp;

      axios.get(this.searchQueryUrlSeries).then((response) => {
        this.seriesResults = response.data.results;
      });
    },
  },
};
</script>

<style lang="scss" scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
::-webkit-scrollbar{
  display: none;
}
#app {
  background-color: rgba(27, 27, 27, 1);
  height: 100vh;
  overflow: auto;
}
</style>