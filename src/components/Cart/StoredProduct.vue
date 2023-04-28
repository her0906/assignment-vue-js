<template>
    <div class="row mt-10">
        <div class="col-md-8">
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

        <div class="col-md-4">
            <base-card>
                <div class="col-12 col-sm-12 col-md-12 col-lg-12 mt-10">
                    <ul class="list-group" v-if="carts.length > 0">
                        <li class="list-group-item bg-success text-white text-center">Your Cart List</li>
                        <cart-list
                        v-for="cart in carts"
                        v-bind:key="cart.id"
                        v-bind:id="cart.id"
                        v-bind:name="cart.name"
                        v-bind:price="cart.price"
                        v-bind:qty="cart.qty"
                        ></cart-list>
                        <li class="list-group-item text-center">
                            <div class="row">
                                <div class="col-5 col-sm-5 col-md-5 col-lg-5 zero">Total Price</div>
                                <div class="col-6 col-sm-6 col-md-6 col-lg-6 zero">Rp{{ totalPrice }}</div>
                            </div>
                        </li>
                    </ul>

                    <ul class="list-group" v-else>
                        <li class="list-group-item bg-warning text-center">Your Cart is Empty!!</li>
                    </ul>
                </div>
            </base-card>
        </div>
    </div>
</template>

<script>
import ProductList from './ProductList.vue';
import CartList from './CartList.vue';

export default {
    inject: ['products', 'carts'],
    components: {
        'product-list': ProductList,
        'cart-list': CartList,
    },

    computed: {
        totalPrice: function() {

            var total = 0;
            this.carts.forEach(item => {
                total += (parseFloat(item.price) * item.qty);
            });

            return total.toFixed(2);
        }
    }
}
</script>

<style scoped>
    .mt-16-m {
        margin-top: -16px;
    }
</style>