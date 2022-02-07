<template>
  <header>
    <div class="d-flex justify-content-between align-items-center py-2">
      <div class="col-8 d-flex align-items-center">
        <div>
          <!-- img by bealabea ;) -->
          <img class="mx-2 logo" src="@/assets/img/boolflix.png" alt="" />
        </div>
        <!-- Bootstrap Navbar -->
        <nav class="navbar navbar-expand-lg navbar-dark">
          <div class="container-fluid">
            <button
              class="navbar-toggler"
              type="button"
              data-bs-toggle="collapse"
              data-bs-target="#navbarSupportedContent"
              aria-controls="navbarSupportedContent"
              aria-expanded="false"
              aria-label="Toggle navigation"
            >
              <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
              <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li class="nav-item">
                  <a
                    @click="$emit('home')"
                    class="nav-link"
                    aria-current="page"
                    href="#"
                    >Home</a
                  >
                </li>
                <li class="nav-item">
                  <a @click="$emit('movies')" class="nav-link active" href="#"
                    >Movies</a
                  >
                </li>
                <li class="nav-item">
                  <a @click="$emit('tvSeries')" class="nav-link" href="#"
                    >TV Series</a
                  >
                </li>
                <li class="nav-item">
                  <a @click="$emit('topRated')" class="nav-link active" href="#"
                    >Top Rated</a
                  >
                </li>
              </ul>
            </div>
          </div>
        </nav>
      </div>
      <div class="col-4 d-flex justify-content-end">
        <!-- Search Lens -->
        <i id="lens" class="fas fa-search p-1" @click="changeBoolean()"></i>
        <!-- Search Input -->
        <input
          v-if="inputBoolean"
          id="search-input"
          class="mx-2 px-2 rounded"
          type="text"
          placeholder="Movies, tv series"
          v-model="keywordSearch"
          @keyup.enter="$emit('search', keywordSearch)"
        />
        <!-- Search Button -->
        <button
          id="search-btn"
          class="mx-2 px-3 py-1 rounded"
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
      inputBoolean: false,
    };
  },
  /* Method for making the search input appear and disappear
  thanks to the click on the search lens  */
  methods: {
    changeBoolean() {
      this.inputBoolean = !this.inputBoolean;
      this.keywordSearch = "";
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/headerStyle.scss";
</style>
