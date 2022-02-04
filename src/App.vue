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
      moviesResult: [],
      tvSeriesResult: [],
      sumResults: [],
      api_key: "fbf42efdae098c0577337b304561e7e9",
    };
  },
  methods: {
    shuffleResult(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        const temp = array[i];
        array[i] = array[j];
        array[j] = temp;
      }
      return array;
    },
    async genericCallApi(type, keyword) {
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
    async callApis(keyword) {
      this.moviesResult = await this.genericCallApi("movie", keyword);
      this.tvSeriesResult = await this.genericCallApi("tv", keyword);
      this.sumResults = [...this.moviesResult, ...this.tvSeriesResult];
      this.sumResults = this.shuffleResult(this.sumResults);
    },
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
