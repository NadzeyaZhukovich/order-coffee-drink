<template>
    <div>
        <BasketListItem
            v-for="(product, index) in drinksInBasket"
            :key="index"
            :product="product"
            @delete-item="deleteItem"
            @delete-product-item="deleteProductItem"
            @add-product-item="addProductItem"/>
    </div>
</template>

<script>
    import BasketListItem from '@/components/BasketListItem';

    export default {
        name: 'BasketList',
        components: {
            BasketListItem,
        },
        props: ['drinksInBasket'],
        methods: {
            deleteItem(id) {
                this.$emit('delete-item', id);
            },

            deleteProductItem(id) {
                this.$emit('delete-product-item', id)
            },

            addProductItem(id) {
              this.$emit('add-product-item', id)
            },
        }
    }
</script>
