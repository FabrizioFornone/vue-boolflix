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
    destructuringAndPush(arrayToDestructured, recipientArray) {
      const [array1, array2] = arrayToDestructured;
      array1.forEach((element) => {
        recipientArray.push(element);
      });
      array2.forEach((element) => {
        recipientArray.push(element);
      });
    },
    shuffleResult(arrayToShuffle) {
      for (let i = arrayToShuffle.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));

        const temp = arrayToShuffle[i];
        arrayToShuffle[i] = arrayToShuffle[j];
        arrayToShuffle[j] = temp;
      }

      return arrayToShuffle;
    },
    callApis(keyword) {
      if (keyword === "") {
        this.sumResults = [];
      } else {
        this.sumResults = [];
        let multiAxios = [
          `https://api.themoviedb.org/3/search/movie/?api_key=fbf42efdae098c0577337b304561e7e9&query=${keyword}`,
          `https://api.themoviedb.org/3/search/tv/?api_key=fbf42efdae098c0577337b304561e7e9&query=${keyword}`,
        ];
        let dataArray = [];
        Promise.all(multiAxios.map((endpoint) => axios.get(endpoint))).then(
          axios.spread((...allData) => {
            allData.forEach((data) => {
              dataArray.push(data.data.results);
            });
            this.destructuringAndPush(dataArray, this.sumResults);
            this.shuffleResult(this.sumResults);
          })
        );
      }
    },
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
