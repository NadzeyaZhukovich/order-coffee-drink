<template>
    <div class="BasketItem_content">
        <span class="BasketItem_product">{{drink.name}}</span>
        <span>
            <button class="BasketItem_counter btn"
                    @click="deleteItem"
            >-</button>
            <span class="BasketItem_quantity">{{quantityCoffee}}</span>
            <button class="BasketItem_counter btn"
                    @click="addItem"
            >+</button>
            <span class="BasketItem_cost">&euro; {{coffeePrice}}</span>
            <button class="BasketItem_delete btn">
                <i class="fa fa-trash" aria-hidden="true"></i>
            </button>
        </span>
    </div>
</template>

<script>
    export default {
        name: 'BasketListItem',
        props: ['drink'],
        data() {
            return {
                quantityCoffee: 1,
            }
        },
        computed: {
            coffeePrice: {
                get() {
                    return this.quantityCoffee * this.drink.price;
                }
            }
        },
        methods: {
            deleteItem() {
                if(this.quantityCoffee > 1) {
                    this.quantityCoffee--;
                } else {
                    this.$emit('delete-item', this.drink.id);
                }
            },
            addItem() {
                if(this.quantityCoffee < 99) {
                    this.quantityCoffee++;
                } else {
                    alert('Too much coffee');
                }
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
