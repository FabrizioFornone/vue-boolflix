<template>
    <div class="card-box">
      <!-- Hover template -->
      <div class="hover-div py-4 px-3">
        <!-- Title -->
        <div class="py-1">
          <strong> <span class="me-1">Titolo:</span> </strong>
          {{ titleProp }} {{ nameProp }}
        </div>
        <!-- Original Title -->
        <div class="py-1">
          <strong> <span class="me-1">Titolo originale:</span> </strong>
          <span> {{ originalTitleProp }} {{ originalNameProp }} </span>
        </div>
        <!-- Vote -->
        <div class="d-flex py-1">
          <strong> <span class="me-1">Voto:</span> </strong>
          <rating-stars :rateNumber="card.vote_average" />
        </div>
        <!-- Language -->
        <div class="py-1">
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
        <!-- Overview -->
        <div class="py-1">
          <strong> <span class="me-1">Overview:</span> </strong>
          <span>{{ card.overview }}</span>
        </div>
      </div>
      <a href="#">
        <!-- Poster -->
        <img
          class="rounded"
          v-if="card.poster_path !== null"
          :src="`https://www.themoviedb.org/t/p/original${card.poster_path}`"
          alt=""
        />
        <!-- Poster IMG not found -->
        <img
          class="rounded"
          v-else
          src="https://www.publicdomainpictures.net/pictures/280000/velka/not-found-image-15383864787lu.jpg"
          alt=""
        />
      </a>
    </div>
</template>

<script>
import ratingStars from "./ratingStars.vue";
export default {
  components: { ratingStars },
  props: {
    card: Object,
    flagsPropCard: Array,
    titleProp: String,
    nameProp: String,
    originalTitleProp: String,
    originalNameProp: String,
  },
  // Method that checks if the language is present between the flags
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
