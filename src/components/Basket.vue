<template>
    <section class="Basket_content">
        <h2 class="Basket_title">Oder coffee drinks</h2>
        <div class="Basket_cost">
            <span>Total cost:</span>
            <span>&euro; {{countTotalCostOfDrinks()}}</span>
        </div>
        <BasketList v-bind:drinksInBasket="drinksInBasket"
                    @delete-item="deleteDrink"
                    @delete-drink-item="deleteDrinkItem"
                    @add-drink-item="addDrinkItem"/>
        <div class="Basket_order">
            <button class="Basket_order--btn"
                    :disabled="!drinksInBasket.length"
                    @click="order">Order
            </button>
        </div>
    </section>
</template>

<script>
    import BasketList from '@/components/BasketList';
    export default {
        name: 'Basket',
        components: {
            BasketList,
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

            countTotalCostOfDrinks() {
                return this.drinksInBasket
                    .map(element => element.drink.price * element.quantity)
                    .reduce((accumulator, currentValue) => accumulator + currentValue, 0)
            },

            order() {
                 this.$emit('order');
                alert('The order is completed');
            }
        }
    }
</script>

<style>
    .Basket_content {
        width: 350px;
        box-shadow:  -1px 0 5px 0 rgba(0, 0, 0, 0.19);
        height: 100%;
        position: fixed;
        display: flex;
        flex: auto;
        flex-direction: column;
        transform: translateX(243%);
    }

    .Basket_title {
        text-align: center;
        padding: 30px 0;
        letter-spacing: 1px;
    }

    .Basket_cost {
        box-shadow: 0 1px 0 rgba(0, 0, 0, 0.1);
        padding: 0 20px 20px;
        display: flex;
        justify-content: space-between;
        font-size: 20px;
    }

    .Basket_order {
        text-align: right;
        padding: 20px;
    }

    .Basket_order--btn {
        padding: 5px;
        cursor: pointer;
        font-size: 16px;
        background-color: rgb(255, 224, 51);
    }
</style>
