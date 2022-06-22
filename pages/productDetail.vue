<template>
  <div class="container">
  <btnReturn />
  <h2>Detail Product</h2>
   <b-button v-on:click="del(product.id)" class="btn btn-danger"
        >Supprimer
    </b-button>
    <b-list-group>
        <b-list-group-item>{{product.id}}</b-list-group-item>
        <b-list-group-item>{{product.name}}</b-list-group-item>
        <b-list-group-item>{{product.price}}</b-list-group-item>
        <b-list-group-item>{{product.description}}</b-list-group-item>
        <b-list-group-item>{{product.is_offer}}</b-list-group-item>
    </b-list-group>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      //items: [],
    };
  },
  async asyncData({ params, $axios }) {
    const product = await $axios.$get(
      `http://localhost:8000/product/${params.id}`
    );
    return { product };
  },
  methods: {
    del(id) {
      axios
        .delete("http://localhost:8000/product/" + id)
        .then((window.location.href = "/"))
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>
<style>
@import "~/assets/style/product.css";
</style>