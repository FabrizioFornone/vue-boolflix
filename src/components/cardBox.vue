<template>
  <div>
    <div class="movie">
      <div class="hover-div border border-white py-4 px-3">
        <div><strong>Titolo:</strong> {{ card.title }}</div>
        <div><strong>Titolo originale:</strong> {{ card.original_title }}</div>
        <div><strong>Voto:</strong> {{ card.vote_average }}</div>
        <div>
          <strong>Lingua:</strong>
          <span
            class="mx-2"
            v-if="langCheck(flagsPropCard, card.original_language)"
          >
            <strong>{{ card.original_language }}</strong>
          </span>
          <img
            v-else
            class="flag mx-2"
            :src="`/flags/${card.original_language}.png`"
            alt=""
          />
        </div>
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
    flagsPropCard: Array,
  },
  methods: {
    langCheck(flag, lang) {
      return !flag.includes(lang);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/cardstyle.scss";
</style>
