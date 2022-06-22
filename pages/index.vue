<template>
    <div class="container">
        <h1>OberjMerch</h1>
        <btnCreate />
        <div v-for="product in products">
            <b-card
                tag="product"
                style="max-width: 20rem;"
                class="mb-2"
            >
                <b-card-text>
                    {{product.name}}
                    {{product.price}}
                    {{product.description}}
                    {{product.is_offer}}
                </b-card-text>
                <b-button :to="{ name: 'productEdit', params: { id: product.id } }" variant="warning">Modifier</b-button>
                <b-button :to="{ name: 'productDetail', params: { id: product.id } }" variant="primary">Detail</b-button>
            </b-card>
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