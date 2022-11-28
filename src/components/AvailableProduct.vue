<template>
  <div class="centering">
    <div class="container">
      <div class="left-container">
        <img :src="details.image" alt="" class="product-image">
      </div>
      <div class="right-container">
        <h1 class="product-name" :class="isMenCategory">{{details.title}}</h1>
        <div class="product-rating-and-category-container">
          <h4 class="category">{{details.category}}</h4>
          <div >
            <ProductRating :productRating="details.rating.rate" :category="details.category"/>
          </div>
        </div>
        <p class="product-description">{{details.description}}</p>
        <h4 class="product-price" :class="isMenCategory">${{details.price}}</h4>
        <div class="button-container">
            <button :class="isMenCtaButton">Buy Now</button>
            <button :class="isMenNextButton" @click="$emit('increase-id')">Next Product</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ProductRating from './ProductRating.vue';

export default {
  props: {
    details: Object
  },
  computed:{
    isMenCategory(){
        return this.details.category === "men's clothing" ? 'men-color' : 'women-color'
    },
    isMenCtaButton(){
        return this.details.category === "men's clothing" ? 'men-cta-button' : 'women-cta-button'
    },
    isMenNextButton(){
        return this.details.category === "men's clothing" ? 'men-next-button' : 'women-next-button'
    },
  },
  components:{
    ProductRating
  }
};
</script>

<style>
@import "../assets/main.css";
</style>