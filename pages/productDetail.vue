<template>
  <div class="container">
  <h2>Detail du produit</h2>
    <b-list-group>
      <b-list-group-item><strong>Nom : </strong>{{product.name}}</b-list-group-item>
      <b-list-group-item><strong>Prix : </strong>{{product.price}}</b-list-group-item>
      <b-list-group-item><strong>Description : </strong>{{product.description}}</b-list-group-item>
      <b-list-group-item><strong>En vente : </strong>{{product.is_offer}}</b-list-group-item>
    </b-list-group>
    <div class="divBtns">
      <btnReturn />
      <b-button v-on:click="del(product.id)" class="btn btn-danger"
          >Supprimer
      </b-button>
    </div>
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
      `https://yd-api-oberjmerch-6mvg7oyrgq-ew.a.run.app/product/${params.id}`
    );
    return { product };
  },
  methods: {
    del(id) {
      axios
        .delete("https://yd-api-oberjmerch-6mvg7oyrgq-ew.a.run.app/product/" + id)
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