<template>
  <div id="app">
    <header-box @search="callApis" />
    <main-component :resultsProp="sumResults" />
  </div>
</template>

<script>
import axios from "axios";
import HeaderBox from "./components/HeaderBox.vue";
import MainComponent from "./components/MainComponent.vue";

export default {
  name: "App",
  components: { HeaderBox, MainComponent },
  data() {
    return {
      moviesFound: [],
      tvSeriesFound: [],
      sumResults: [],
    };
  },
  methods: {
    callApiFilm(keyword) {
      if (keyword === "") {
        this.moviesFound = [];
      } else {
        axios
          .get(
            `https://api.themoviedb.org/3/search/movie/?api_key=fbf42efdae098c0577337b304561e7e9&query=${keyword}`
          )
          .then((response) => {
            this.moviesFound = response.data.results;
          });
      }
    },
    callApiSeries(keyword) {
      if (keyword === "") {
        this.tvSeriesFound = [];
      } else {
        axios
          .get(
            `https://api.themoviedb.org/3/search/tv/?api_key=fbf42efdae098c0577337b304561e7e9&query=${keyword}`
          )
          .then((response) => {
            this.tvSeriesFound = response.data.results;
          });
      }
    },
    callApis(keywordApi) {
      this.callApiFilm(keywordApi);
      this.callApiSeries(keywordApi);
      this.sumResults = [...this.moviesFound, ...this.tvSeriesFound];
      this.sumResults = this.shuffleResult(this.sumResults);
    },
    shuffleResult(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));

        const temp = array[i];
        array[i] = array[j];
        array[j] = temp;
      }

      return array;
    },
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
