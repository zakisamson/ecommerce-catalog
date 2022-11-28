<script>
import AvailableProduct from "./AvailableProduct.vue";
import UnavailableProduct from "./UnavailableProduct.vue";

export default {
  data() {
    return {
      dataId: 1,
      productDetails: Object,
      loading: true,
      available: true
    };
  },
  mounted() {
    this.getData(16);
  },
  methods: {
    async getData(id) {
      this.loading = true;
      try {
        const response = await fetch(`https://fakestoreapi.com/products/${id}`);
        const results = await response.json();
        this.productDetails = results;
        console.log(this.productDetails)
        if(this.productDetails.category === "men's clothing" || this.productDetails.category === "women's clothing"){
            this.available = true
        } else {
            this.available = false
        }
      } catch (err) {
        console.log(err);
      } finally {
        this.loading = false;
      }
    },
    increaseId() {
      this.dataId < 20 ? this.dataId++ : (this.dataId = 1);
      this.getData(this.dataId);
    },
  },
  components: {
    AvailableProduct,
    UnavailableProduct
  },
  computed:{
    menBackground(){
        if(!this.available) return ''
        return this.productDetails.category === "men's clothing" ? "men-background" : "women-background"
    }
  }
};
</script>

<template >
  <div class="main-layout">
    <div v-if="loading" class="loader"></div>
    <div :class="menBackground" class="default">
        <img v-if="available" src="../assets/backgroundPattern.png" alt="" style="object-fit: cover; width: 100%; ">
    </div>
    <AvailableProduct
      v-if="!loading && available"
      :details="productDetails"
      @increase-id="increaseId"
    />
    <UnavailableProduct
      v-if="!loading && !available"
      @increase-id="increaseId"
    />
  </div>
</template>

<style>
@import "../assets/main.css";

/* .background-pattern {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.background {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50%;
  width: 100%;
} */
</style>