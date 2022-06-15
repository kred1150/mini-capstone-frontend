<script>
import axios from "axios";

export default {
  data: function () {
    return {
      products: [],
    };
  },
  created: function () {},
  methods: {
    indexProducts: function () {
      axios.get("/products.json").then((response) => {
        console.log("products index", response);
        this.products = response.data;
      });
    },
  },
};
</script>

<template>
  <div class="about">
    <h1>
      <button v-on:click="indexProducts()">Show All Products</button>
      <div v-for="product in products" v-bind:key="product.id">
        <h3>{{ product.name }}</h3>
        <h5>${{ product.price }}</h5>
        <p>Description: {{ product.description }}</p>
        <!-- <div v-for="image in images" v-bind:key="image.id">
          <p>{{ image.id }}</p>
          <img src="`image.image_url`" alt="" />
        </div> -->
      </div>
    </h1>
  </div>
</template>

<style></style>
