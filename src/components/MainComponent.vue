<template>
  <main>
    <div class="container py-4">
      <div class="row flex-wrap mb-5">
        <div
          class="col-6 col-md-4 col-lg-3 col-xxl-2 my-3"
          v-for="element in resultsProp"
          :key="element.id"
        >
          <card-box
            :card="element"
            :flagsPropCard="flagsProp"
            :titleProp="element.title"
            :nameProp="element.name"
            :originalTitleProp="element.original_title"
            :originalNameProp="element.original_name"
          />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import cardBox from "./cardBox.vue";
export default {
  components: { cardBox },
  props: {
    resultsProp: Array,
    flagsProp: Array,
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/mainComponentStyle.scss";
</style>
