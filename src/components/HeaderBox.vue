<template>
  <header>
    <div class="d-flex justify-content-between align-items-center py-3">
      <!-- img by bealabea ;) -->
      <img class="mx-5" src="@/assets/img/boolflix.png" alt="" />
      <div>
        <i class="fas fa-search p-1" @click="$emit('inputVisible')"></i>
        <input
          v-if="inputProp"
          id="search-input"
          class="mx-2 px-2 rounded"
          type="text"
          placeholder="Movies, tv series"
          v-model="keywordSearch"
          @keyup.enter="$emit('search', keywordSearch)"
        />
        <button
          id="search-btn"
          class="mx-4 px-3 py-1 rounded"
          @click="$emit('search', keywordSearch)"
        >
          Search
        </button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      keywordSearch: "",
    };
  },
  props: {
    inputProp: Boolean,
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/headerStyle.scss";
</style>
