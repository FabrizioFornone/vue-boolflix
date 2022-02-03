<template>
  <header>
    <div class="d-flex justify-content-between align-items-center py-3">
      <!-- img by bealabea ;) -->
      <img class="mx-4" src="@/assets/img/boolflix.png" alt="" />
      <div>
        <input
          id="search-input"
          class="mx-2 py-1 px-2 rounded-pill"
          type="text"
          placeholder="Search"
          v-model="keywordSearch"
          @keyup.enter="$emit('search', keywordSearch)"
        />
        <button
          id="search-btn"
          class="mx-4 py-1 px-3 rounded-pill"
          @click="$emit('search', keywordSearch)"
        >
          Start!
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
};
</script>

<style lang="scss" scoped>
@import "@/style/headerStyle.scss";
</style>
