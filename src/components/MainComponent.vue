<template>
  <main>
    <div class="container py-4">
      <div class="row flex-wrap">
        <div class="col-2 my-2" v-for="element in resultsProp" :key="element.id">
          <card-box :card="element" />
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
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/mainComponentStyle.scss";
</style>
