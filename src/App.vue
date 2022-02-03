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
      sumResults: [],
    };
  },
  methods: {
    callApis(keyword) {
      if (keyword === "") {
        this.moviesFound = [];
      } else {
        this.sumResults = [];
        let multiAxios = [
          `https://api.themoviedb.org/3/search/movie/?api_key=fbf42efdae098c0577337b304561e7e9&query=${keyword}`,
          `https://api.themoviedb.org/3/search/tv/?api_key=fbf42efdae098c0577337b304561e7e9&query=${keyword}`,
        ];
        let array = [];
        Promise.all(multiAxios.map((endpoint) => axios.get(endpoint))).then(
          axios.spread((...allData) => {
            allData.forEach((data) => {
              array.push(data.data.results);
            });
            const [array1, array2] = array;
            array1.forEach((element) => {
              this.sumResults.push(element);
            });
            array2.forEach((element) => {
              this.sumResults.push(element);
            });
            this.shuffleResult(this.sumResults);
          })
        );
      }
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
