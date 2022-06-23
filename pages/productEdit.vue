<template>
<div>
<Header />
  <div class="container">
  <h2>Modifier le produit : {{product.name}}</h2>
  <b-form @submit="up(product.id)" v-bind:key="product.id">       
        <b-form-group label="Nom" label-for="input">
            <b-form-input
                v-model="product.name"
                placeholder="Nom"
            ></b-form-input>
        </b-form-group>
        
        <b-form-group label="Prix" label-for="input">
            <b-form-input
                v-model="product.price"
                placeholder="prix"
            ></b-form-input>
        </b-form-group>

        <b-form-group label="Description" label-for="input">
            <b-form-input
                v-model="product.description"
                placeholder="description"
            ></b-form-input>
        </b-form-group>
        <label>En vente</label>
        <b-input-group label="En vente" class="input">
                <b-input-group-prepend is-text>
                  <b-form-checkbox
                    v-model="product.is_offer"
                    type="checkbox"
                    value="true"
                    unchecked-value="false"
                  ></b-form-checkbox>
                </b-input-group-prepend>
                <b-form-input class="champs" v-model="product.is_offer">{{
                  is_offer
                }}</b-form-input>
              </b-input-group>
        <btnReturn />
        <b-button type="submit" variant="primary">Enregistrer</b-button>
    </b-form>
  </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data(){
      return{
        'product.is_offer':"true"
      }
  },
  async asyncData({ params, $axios }) {
    const product = await $axios.$get(
      `https://yd-api-oberjmerch-6mvg7oyrgq-ew.a.run.app/products/${params.id}`
    );
    return { product };
  },
  methods: {
    up(id) {
      axios
        .put("https://yd-api-oberjmerch-6mvg7oyrgq-ew.a.run.app/products/" + id, { 
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