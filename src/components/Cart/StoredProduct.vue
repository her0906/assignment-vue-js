<template>
    <div class="row mt-10">
        <div class="col">
            <base-card>
                <product-list
                v-for="product in products"
                v-bind:key="product.id"
                v-bind:id="product.id"
                v-bind:name="product.name"
                v-bind:price="product.price"
                v-bind:image="product.image"
                v-bind:qty="product.qty"
                ></product-list>
            </base-card>
        </div>
    </div>
</template>

<script>
import ProductList from './ProductList.vue';

export default {
    inject: ['products'],
    components: {
        'product-list': ProductList,
    },
}
</script>

<style scoped>
    .mt-16-m {
        margin-top: -16px;
    }
</style>