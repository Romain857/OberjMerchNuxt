<template>
<div>
<Header />
  <div class="container">
        <b-form @submit.prevent="submit">
          <b-container fluid>
            <h2 id="title">Ajouter un produit</h2>
            <b-row class="my-3">

            <b-input-group class="input" >
                <template #prepend>
                  <b-input-group-text class="label"
                    >Nom</b-input-group-text
                  >
                </template>
                <b-form-input
                  class="champs"
                  v-model="name"
                  required
                ></b-form-input>
              </b-input-group>

              <b-input-group class="input">
                <template #prepend>
                  <b-input-group-text class="label"
                    >Prix</b-input-group-text
                  >
                </template>
                <b-form-input
                  type="number"
                  class="champs"
                  v-model="price"
                  required
                ></b-form-input>
              </b-input-group>

              <b-input-group class="input">
                <template #prepend>
                  <b-input-group-text class="label"
                    >Description</b-input-group-text
                  >
                </template>
                <b-form-input
                  class="champs"
                  v-model="description"
                  required
                ></b-form-input>
              </b-input-group>
    
              <b-input-group class="input">
                <template #prepend>
                  <b-input-group-text class="label">En vente</b-input-group-text>
                </template>
                <b-input-group-prepend is-text>
                  <b-form-checkbox
                    v-model="is_offer"
                    type="checkbox"
                    value="true"
                    unchecked-value="false"
                  ></b-form-checkbox>
                </b-input-group-prepend>
                <b-form-input class="champs" v-model="is_offer">{{
                  is_offer
                }}</b-form-input>
              </b-input-group>
            </b-row>
          </b-container>
          <btnReturn />
          <b-button id="submit" type="submit" variant="primary"
            >Ajouter</b-button
          >
        </b-form>
  </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
    data(){
        return{
            name:"",
            price:"",
            description:"",
            is_offer:"true"
        }
    },
  methods: {
    submit() {
      axios
        .post("https://yd-api-oberjmerch-6mvg7oyrgq-ew.a.run.app/products", {
          name: this.name,
          price: this.price,
          description: this.description,
          is_offer: this.is_offer
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

<style scoped>
@import "~/assets/style/product.css";
</style>