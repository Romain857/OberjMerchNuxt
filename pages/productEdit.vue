<template>
  <div class="container">
  <h2>Edit Product {{product.name}}</h2>
  <b-form @submit="up(product.id)" v-bind:key="product.id">       
        <b-form-group id="input-group" label="Name" label-for="input">
            <b-form-input
                v-model="product.name"
                placeholder="name"
            ></b-form-input>
        </b-form-group>
        
        <b-form-group id="input-group" label="Price" label-for="input">
            <b-form-input
                v-model="product.price"
                placeholder="price"
            ></b-form-input>
        </b-form-group>

        <b-form-group id="input-group" label="Description" label-for="input">
            <b-form-input
                v-model="product.description"
                placeholder="description"
            ></b-form-input>
        </b-form-group>

        <b-form-group id="input-group" label="Is_offer" label-for="input">
            <b-form-input
                v-model="product.is_offer"
                placeholder="is_offer"
            ></b-form-input>
        </b-form-group>
        <btnReturn />
        <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async asyncData({ params, $axios }) {
    const product = await $axios.$get(
      `http://localhost:8000/product/${params.id}`
    );
    return { product };
  },
  methods: {
    up(id) {
      axios
        .put("http://localhost:8000/product/" + id, {
          id: this.product.id,
          name: this.product.name,
          price: this.product.price,
          description: this.product.description,
          is_offer: this.product.is_offer,
        })
        .then(
          function (response) {
            window.location.href = "/";
          }.bind(this)
        );
    },
  },
};
</script>
<style>
@import "~/assets/style/product.css";
</style>