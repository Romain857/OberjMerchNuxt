<template>
  <div class="container">
  <btnReturn />
        <b-form @submit.prevent="submit">
          <b-container fluid>
            <h2 id="title">New Product</h2>
            <b-row class="my-3">

            <b-input-group >
                <template #prepend>
                  <b-input-group-text
                    >Name</b-input-group-text
                  >
                </template>
                <b-form-input
                  v-model="name"
                  required
                ></b-form-input>
              </b-input-group>

              <b-input-group >
                <template #prepend>
                  <b-input-group-text
                    >Price</b-input-group-text
                  >
                </template>
                <b-form-input
                  v-model="price"
                  required
                ></b-form-input>
              </b-input-group>

              <b-input-group >
                <template #prepend>
                  <b-input-group-text
                    >Description</b-input-group-text
                  >
                </template>
                <b-form-input
                  v-model="description"
                  required
                ></b-form-input>
              </b-input-group>

              <b-input-group >
                <template #prepend>
                  <b-input-group-text
                    >Image</b-input-group-text
                  >
                </template>
                <b-form-input
                  v-model="img"
                  required
                ></b-form-input>
              </b-input-group>

                <b-input-group >
                <template #prepend>
                  <b-input-group-text
                    >Is_offer</b-input-group-text
                  >
                </template>
                <b-form-input
                  v-model="is_offer"
                  required
                ></b-form-input>
              </b-input-group>

            </b-row>
          </b-container>
          <b-button id="submit" type="submit" variant="primary"
            >Submit</b-button
          >
        </b-form>
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
            img:"",
            is_offer:""
        }
    },
  methods: {
    submit() {
      axios
        .post("http://localhost:8000/product", {
          name: this.name,
          price: this.price,
          description: this.description,
          img: this.img,
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