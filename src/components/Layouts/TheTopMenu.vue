<template>
    <div class="row">
        <div class="col">
            <button type="button" class="btn btn-info btn-md btn-block" v-on:click="selectTab('add-product')">Cart List</button>
        </div>
    </div>
</template>

<script>
export default {
    inject:['setSelectedTab'],
    methods: {
        selectTab: function(tab) {
            this.setSelectedTab(tab);
        }
    },
}
</script>

<style scoped>
    .btn-active-store {
        color: #fff;
        background-color: #007bff;
        border-color: #007bff;
    }

    .btn-active-add {
        color: #fff;
        background-color: #17a2b8;
        border-color: #17a2b8;
    }
</style>