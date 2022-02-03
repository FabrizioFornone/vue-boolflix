<template>
  <main>
    <div class="container py-4">
      <div class="row flex-wrap">
        <div
          class="movie col-2 my-2"
          v-for="movie in moviesProp"
          :key="movie.id"
        >
          <div class="hover-div py-4 px-3">
            <div><strong>Titolo:</strong> {{ movie.title }}</div>
            <div>
              <strong>Titolo originale:</strong> {{ movie.original_title }}
            </div>
            <div><strong>Voto:</strong> {{ movie.vote_average }}</div>
            <div><strong>Overview:</strong> {{ movie.overview }}</div>
          </div>
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
