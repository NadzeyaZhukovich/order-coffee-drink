<template>
    <div>
        <BasketListItem
            v-for="(product, index) in drinksInBasket"
            :key="index"
            :product="product"
            @delete-item="deleteItem"/>
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
            }
        }
    }
</script>
