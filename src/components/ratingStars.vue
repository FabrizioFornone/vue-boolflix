<template>
  <div>
    <i class="star fas fa-star" v-for="(star, index) in stars()" :key="index">
    </i>
  </div>
</template>

<script>
export default {
  props: {
    rateNumber: Number,
  },
  methods: {
    stars() {
      return Math.round(this.rateNumber / 2);
    },
  },
};
</script>

<style lang="scss" scoped>
.star {
  margin: 0 1px;
  font-size: 11px;
}
</style>
