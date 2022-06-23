<template>
<div>
<Header />
<br>
<div class="container">
<h2>Liste des produits</h2>
<btnCreate />
    <div id="dash">
        <div v-for="product in products">
            <b-card
                id="card"
                tag="product"
                style="max-width: 20rem;"
                class="mb-2"
            >
                <b-card-text>
                    Produit : <strong>{{product.name}}</strong>
                </b-card-text>
                <b-img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQxL0Klx53RUk-t4EM-SJm2vnrAhNbvg5uVb_euJaCGW894B7Fs6bKqQx7lD8OGzYZSKb8&usqp=CAU"></b-img>
                <b-button :to="{ name: 'productEdit', params: { id: product.id } }" variant="warning">Modifier</b-button>
                <b-button :to="{ name: 'productDetail', params: { id: product.id } }" variant="primary">Detail</b-button>
            </b-card>
        </div>
    </div>
    <Footer />
    </div>
    </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {};
  },
  async asyncData({ params, $axios }) {
    const products = await $axios.$get('https://yd-api-oberjmerch-6mvg7oyrgq-ew.a.run.app/products');
    return { products };
  },
};
</script>

<style scoped>
@import "~/assets/style/product.css";
</style>