<template>
  <header>
    <div class="d-flex justify-content-between align-items-center py-2">
      <!-- img by bealabea ;) -->
      <div class="col-8 d-flex align-items-center">
        <div>
          <img class="mx-2 logo" src="@/assets/img/boolflix.png" alt="" />
        </div>
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
                  <a class="nav-link " aria-current="page" href="#"
                    >Home</a
                  >
                </li>
                <li class="nav-item">
                  <a class="nav-link " href="#">Serie TV</a>
                </li>
                <li class="nav-item">
                  <a class="nav-link active" href="#">Originali</a>
                </li>
                <li class="nav-item">
                  <a class="nav-link active" href="#">Aggiunti di recente</a>
                </li>
                <li class="nav-item">
                  <a class="nav-link active" href="#">La mia lista</a>
                </li>
              </ul>
            </div>
          </div>
        </nav>
      </div>
      <div class="col-4 d-flex justify-content-end">
        <i id="lens" class="fas fa-search p-1" @click="changeBoolean()"></i>
        <input
          v-if="inputBoolean"
          id="search-input"
          class="mx-2 px-2 rounded"
          type="text"
          placeholder="Movies, tv series"
          v-model="keywordSearch"
          @keyup.enter="$emit('search', keywordSearch)"
        />
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
