<template>
  <div class="container">
  <h2>Modifier un produit : {{product.name}}</h2>
  <b-form @submit="up(product.id)" v-bind:key="product.id">       
        <b-form-group id="input-group" label="Nom" label-for="input">
            <b-form-input
                v-model="product.name"
                placeholder="Nom"
            ></b-form-input>
        </b-form-group>
        
        <b-form-group id="input-group" label="Prix" label-for="input">
            <b-form-input
                v-model="product.price"
                placeholder="prix"
            ></b-form-input>
        </b-form-group>

        <b-form-group id="input-group" label="Description" label-for="input">
            <b-form-input
                v-model="product.description"
                placeholder="description"
            ></b-form-input>
        </b-form-group>

        <b-form-group id="input-group" label="En vente" label-for="input">
            <b-form-input
                v-model="product.is_offer"
                placeholder="En vente"
            ></b-form-input>
        </b-form-group>
        <btnReturn />
        <b-button type="submit" variant="primary">Enregistrer</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async asyncData({ params, $axios }) {
    const product = await $axios.$get(
      `https://yd-api-oberjmerch-6mvg7oyrgq-ew.a.run.app/product/${params.id}`
    );
    return { product };
  },
  methods: {
    up(id) {
      axios
        .put("https://yd-api-oberjmerch-6mvg7oyrgq-ew.a.run.app/product/" + id, {
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