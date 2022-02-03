<template>
  <div id="app">
    <header-box @search="callApi" />
    <main-component :moviesProp="moviesFound" />
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
    };
  },
  methods: {
    callApi(keyword) {
      if (keyword === "") {
        this.moviesFound = [];
        alert('Non hai cercato nulla!')
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
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
