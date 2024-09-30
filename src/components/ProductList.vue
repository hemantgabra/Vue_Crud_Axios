<template>
    <div>
        <h1>Product List</h1>
        <div class="product-grid">
            <ProductCard v-for="product in products" :key="product.id" :product=""prodcut />
        </div>
    </div> 
</template>


<script>
import axios from 'axios';
import ProductCard from './ProductCard.vue';


export default {
    components: {
        ProductCard
    },
    data() { 
        return {
            products: []
        };
    },
    mounted() { 
        this.fetchProducts();
    },
    methods: {
        async fetchProducts() {
            const response = await axios.get('https://fakestoreapi.com/products');
            this.products = response.data;
        }
    }
}