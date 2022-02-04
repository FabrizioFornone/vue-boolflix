<template>
  <div>
    <div class="movie">
      <div class="hover-div py-4 px-3">
        <div>
          <strong> <span class="me-1">Titolo:</span> </strong>
          {{ titleProp }} {{ nameProp }}
        </div>
        <div>
          <strong> <span class="me-1">Titolo originale:</span> </strong>
          <span> {{ originalTitleProp }} {{ originalNameProp }} </span>
        </div>
        <div>
          <strong> <span class="me-1">Voto:</span> </strong>
          <span
            class="star"
            v-for="(star, index) in Math.round(card.vote_average / 2)"
            :key="index"
            >&#9733;</span
          >
        </div>
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
        <div>
          <strong> <span class="me-1">Overview:</span> </strong>
          <span>{{ card.overview }}</span>
        </div>
      </div>
      <a href="#">
        <img
          class="rounded"
          v-if="card.poster_path !== null"
          :src="`https://www.themoviedb.org/t/p/original${card.poster_path}`"
          alt=""
        />
        <img
          class="rounded"
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
    titleProp: String,
    nameProp: String,
    originalTitleProp: String,
    originalNameProp: String,
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
