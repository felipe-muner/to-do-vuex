<template>
  <div id="product-list-one">
    <h2>Product List One</h2>
    <ul>
      <li v-for="product in saleProducts" v-bind:key="product.id">
        <!-- <li v-for="(product, i) in saleProducts" v-bind:key="product.id">  -->
        <span class="name">{{product.name}}</span>&nbsp;
        <span class="price">U${{product.price}}</span>
      </li>
    </ul>
    <button v-on:click="reducePrice(4)">Reduce Price</button>
    - {{products}} -
  </div>
</template>

<script>
import { mapState } from "vuex";
import { mapGetters } from "vuex";
import { mapActions } from "vuex";

export default {
  computed: {
    // products() {
    //   return this.$store.state.products;
    // },
    ...mapState(["products"]),
    ...mapGetters(["saleProducts"])
    // saleProducts() {
    //   return this.$store.getters.saleProducts;
    // }
  },
  methods: {
    ...mapActions(["reducePrice"])
    // reducePrice: function(amount) {
    //   // this.$store.commit('reducePrice', amount); // straight to mutation (NOT NICE)
    //   this.$store.dispatch("reducePrice", amount);
    // }
  }
};
</script>

<style scoped>
#product-list-one {
  background: #fff8b1;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.2);
  margin-bottom: 30px;
  padding: 10px 20px;
}
#product-list-one ul {
  padding: 0;
}
#product-list-one li {
  display: inline-block;
  margin-right: 10px;
  margin-top: 10px;
  padding: 20px;
  background: rgba(255, 255, 255, 0.7);
}
.price {
  font-weight: bold;
  color: #e8800c;
}
</style>
