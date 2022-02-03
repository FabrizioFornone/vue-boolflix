<template>
  <main>
    <div class="container py-4">
      <div class="row flex-wrap">
        <div v-for="movie in moviesProp" :key="movie.id">
          <card-box :card="moviesProp" />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import cardBox from "./cardBox.vue";
export default {
  components: { cardBox },
  props: {
    moviesProp: Array,
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/mainComponentStyle.scss";
</style>
