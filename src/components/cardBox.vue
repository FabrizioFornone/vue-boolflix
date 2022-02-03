<template>
  <div>
    <div class="movie">
      <div class="hover-div border border-white py-4 px-3">
        <div><strong>Titolo:</strong> {{ card.title }}</div>
        <div><strong>Titolo originale:</strong> {{ card.original_title }}</div>
        <div><strong>Voto:</strong> {{ card.vote_average }}</div>
        <div><strong>Lingua:</strong> {{ card.original_language }}</div>
        <div><strong>Overview:</strong> {{ card.overview }}</div>
      </div>
      <a href="#">
        <img
          v-if="card.poster_path !== null"
          :src="`https://www.themoviedb.org/t/p/original${card.poster_path}`"
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
</template>

<script>
export default {
  props: {
    card: Object,
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/cardstyle.scss";
</style>
