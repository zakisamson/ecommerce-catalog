<template>
  <div class="product-rating-container">
    <p>
      <span class="product-rating">{{ this.productRating }}</span
      >/5
    </p>
    <div class="rating-container">
      <div v-for="rating in maxRating" :key="rating">
        <div :class="rating <= ratingRounded ? fullClass : nullClass"></div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    productRating: Number,
    category: String,
  },
  computed: {
    ratingRounded() {
      return Math.round(this.productRating);
    },
    isMen() {
      return this.category === "men's clothing";
    },
    fullClass() {
      return this.isMen ? "men-rating-full" : "women-rating-full";
    },
    nullClass() {
      return this.isMen ? "men-rating-null" : "women-rating-null";
    },
  },
  data() {
    return {
      maxRating: 5,
    };
  },
};
</script>
<style>
@import "../assets/main.css";

.rating-container {
  display: flex;
  width: 50%;
  align-items: center;
  gap: 2px;
  margin-left: 10px;
}
</style>