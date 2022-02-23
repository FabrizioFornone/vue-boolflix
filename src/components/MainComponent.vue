<template>
  <main>
    <div class="container py-4">
      <div class="row flex-wrap mb-4">
        <div
          class="col-6 col-md-4 col-lg-3 col-xxl-2 my-3"
          v-for="element in resultsProp"
          :key="element.id"
        >
        <!-- Card Component  -->
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
import CardBox from "./CardBox.vue";
export default {
  components: { CardBox },
  props: {
    resultsProp: Array,
    flagsProp: Array,
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/mainComponentStyle.scss";
</style>
