<template>
    <div class="row mt-10">
        <div class="col">
            <base-card>
            <button type="button" class="btn btn-info btn-md btn-block" v-on:click="selectTab('stored-product')">Back To Product List</button>
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
import CartList from './CartList.vue';

export default {
    inject: ['storeProduct' , 'setSelectedTab' , 'carts'],
    components: {
        'cart-list': CartList,
    },
    data: function(){
        return {
            isRequired: false,
        }
    },
    computed: {
        totalPrice: function() {

            var total = 0;
            this.carts.forEach(item => {
                total += (parseFloat(item.price) * item.qty);
            });

            return total.toFixed(2);
        }
    },
    methods: {
        selectTab: function(tab) {
            this.setSelectedTab(tab);
        },
        addProduct: function() {
            const product_name = this.$refs.product_name.value;
            const price = this.$refs.price.value;
            const quantity = this.$refs.quantity.value;

            if (product_name.trim() === '' || price.trim() === '' || quantity.trim() === '') {
                this.isRequired = true;
                return;
            }

            this.storeProduct(product_name, price, quantity);
        }
    },
}
</script>

<style scoped>
    .required{
        color: red;
        font-weight: 700;
    }
</style>