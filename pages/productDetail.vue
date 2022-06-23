<template>
<div>
<Header />
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

      <b-button
                class="btn"
                id="btnDelTicket"
                variant="danger"
                @click="$bvToast.show('delete')"
              >
               Supprimer
              </b-button>
      <b-toast id="delete" title="Delete" static no-auto-hide>
                Etes-vous sur de vouloir supprimer ce ticket : <strong>{{product.name}}</strong> ?
                <a v-on:click="del(product.id)" id="del" class="btn btn-primary link"
                  >Valider</a
                >
      </b-toast>
    </div>
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
    confirmDelete() {
      return confirm("Etes vous sur de vouloir delete ce ticket ?");
    },
  },
};
</script>
<style>
@import "~/assets/style/product.css";
</style>