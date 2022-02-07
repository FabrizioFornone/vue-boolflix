<template>
  <div id="app">
    <header-box
      @search="searchCallMethod"
      @home="homeMix"
      @movies="mostViewedMovies"
      @tvSeries="mostViewedTV"
      @topRated="topRated"
    />
    <main-component :resultsProp="sumResults" :flagsProp="flagsArray" />
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
      moviesResult: [],
      tvSeriesResult: [],
      sumResults: [],
      api_key: "fbf42efdae098c0577337b304561e7e9",
      flagsArray: ["de", "en", "es", "fr", "it"],
    };
  },
  methods: {
    // Method for shuffling elements into an array
    shuffleResult(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        const temp = array[i];
        array[i] = array[j];
        array[j] = temp;
      }
      return array;
    },
    // Method to call elements with a keyword from themoviedb API
    async searchCallApi(type, keyword) {
      const params = {
        query: keyword,
        api_key: this.api_key,
      };

      const results = await axios
        .get(`https://api.themoviedb.org/3/search/${type}`, { params })
        .then((res) => {
          return res.data.results;
        });
      return results;
    },
    // Method to call most viewed elements from themoviedb API
    callAPI(type, criteria, n) {
      axios
        .get(
          `https://api.themoviedb.org/3/${type}/${criteria}?api_key=ad1668ee1fca2cd9ebdd9b7319f4ce6c`
        )
        .then((res) => {
          for (let i = 0; i < n; i++) {
            this.sumResults.push(res.data.results[i]);
          }
          this.sumResults = this.shuffleResult(this.sumResults);
        });
    },
    // Method linked to Home button
    homeMix() {
      this.sumResults = [];
      this.callAPI("movie", "popular", 6);
      this.callAPI("tv", "popular", 6);
    },
    // Method linked to Movies button
    mostViewedMovies() {
      this.sumResults = [];
      this.callAPI("movie", "popular", 12);
    },
    // Method linked to Tv Series button
    mostViewedTV() {
      this.sumResults = [];
      this.callAPI("tv", "popular", 12);
    },
    // Method linked to Top Rated button
    topRated() {
      this.sumResults = [];
      this.callAPI("movie", "top_rated", 6);
      this.callAPI("tv", "top_rated", 6);
    },
    // Method linked to search bar and search button
    async searchCallMethod(keyword) {
      this.sumResults = [];
      this.moviesResult = await this.searchCallApi("movie", keyword);
      this.tvSeriesResult = await this.searchCallApi("tv", keyword);
      this.sumResults = [...this.moviesResult, ...this.tvSeriesResult];
      this.sumResults = this.shuffleResult(this.sumResults);
    },
  },
  mounted() {
    this.homeMix();
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
