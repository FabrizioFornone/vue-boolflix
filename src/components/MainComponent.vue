<template>
  <main>
    <div class="container py-4">
      <div class="row flex-wrap">
        <div
          class="movie col-2 my-2"
          v-for="movie in moviesProp"
          :key="movie.id"
        >
          <div class="hover-div border border-white py-4 px-3">
            <div><strong>Titolo:</strong> {{ movie.title }}</div>
            <div>
              <strong>Titolo originale:</strong> {{ movie.original_title }}
            </div>
            <div><strong>Voto:</strong> {{ movie.vote_average }}</div>
            <div><strong>Overview:</strong> {{ movie.overview }}</div>
          </div>
          <a href="#">
            <img
              v-if="movie.poster_path !== null"
              :src="`https://www.themoviedb.org/t/p/original${movie.poster_path}`"
              alt=""
            />
            <img
              v-else
              src="https://www.publicdomainpictures.net/pictures/280000/velka/not-found-image-15383864787lu.jpg"
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
