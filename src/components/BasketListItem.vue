<template>
    <div class="BasketItem_content">
        <span class="BasketItem_product">{{product.drink.name}}</span>
        <span>
            <button class="BasketItem_counter btn"
                    @click="deleteDrinkItem">-
            </button>
            <span class="BasketItem_quantity">{{product.quantity}}</span>
            <button class="BasketItem_counter btn"
                    @click="addDrinkItem">+
            </button>
            <span class="BasketItem_cost">&euro; {{product.drink.price}}</span>
            <button class="BasketItem_delete btn"
                    @click="deleteDrink">
                <i class="fa fa-trash" aria-hidden="true"></i>
            </button>
        </span>
    </div>
</template>

<script>
    export default {
        name: 'BasketListItem',
        props: ['product'],
        methods: {
            deleteDrinkItem() {
                this.$emit('delete-drink-item', this.product.drink.id);
            },

            addDrinkItem() {
                this.$emit('add-drink-item', this.product.drink.id);
            },

            deleteDrink() {
                this.$emit('delete-item', this.product.drink.id);
            }
        }
    }
</script>

<style>
    .BasketItem_content {
        padding: 7px 20px;
        font-size: 18px;
        display: flex;
        justify-content: space-between;
    }

    .BasketItem_product {
        font-size: 16px;
        letter-spacing: 1px;
        flex-wrap: wrap;
    }

    .BasketItem_counter {
        width: 20px;
    }

    .BasketItem_quantity {
        margin: 10px;
        font-size: 16px;
    }

    .BasketItem_cost {
        margin: 0 10px;
        font-size: 16px;
    }

    .BasketItem_delete {
        border: none;
    }

    .btn {
        background: none;
        cursor: pointer;
        font-size: 16px;
    }
</style>
