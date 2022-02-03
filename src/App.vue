<template>
  <div id="app">
    <header-box />
    <main-component />
  </div>
</template>

<script>
import HeaderBox from "./components/HeaderBox.vue";
import MainComponent from "./components/MainComponent.vue";

export default {
  name: "App",
  components: { HeaderBox, MainComponent },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
