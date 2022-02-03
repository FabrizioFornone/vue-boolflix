<template>
  <header>
    <div class="d-flex justify-content-between align-items-center pt-3 pb-2">
      <h2 class="text-uppercase mx-4">boolflix</h2>
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
          class="mx-4 py-1 px-2 rounded-pill"
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
