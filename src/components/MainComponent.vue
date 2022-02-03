<template>
  <main>
    <div class="container py-4">
      <div class="row flex-wrap">
        <div class="col-2" v-for="movie in moviesProp" :key="movie.id">
          <a href="#">
            <img
              :src="`https://www.themoviedb.org/t/p/w300_and_h450_bestv2${movie.poster_path}`"
              alt=""
            />
          </a>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  props: {
    moviesProp: Array,
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/mainComponentStyle.scss";
</style>
