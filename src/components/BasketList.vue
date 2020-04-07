<template>
    <div>
        <BasketListItem
            v-for="(product, index) in drinksInBasket"
            :key="index"
            :product="product"
            @delete-item="deleteDrink"
            @delete-drink-item="deleteDrinkItem"
            @add-drink-item="addDrinkItem"/>
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
            deleteDrink(id) {
                this.$emit('delete-item', id);
            },

            deleteDrinkItem(id) {
                this.$emit('delete-drink-item', id)
            },

            addDrinkItem(id) {
              this.$emit('add-drink-item', id)
            },
        }
    }
</script>
