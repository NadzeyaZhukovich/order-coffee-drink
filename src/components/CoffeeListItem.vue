<template>
    <li class="CoffeeDrink_content">
        <div class="CoffeeDrink_iconBox">
            <img
              class="CoffeeDrink_icon"
              v-bind:src="coffee.image">
        </div>

        <div class="CoffeeDrink_information">
            <span class="CoffeeDrink_name"><b>{{coffee.name}}</b></span>
            <span class="CoffeeDrink_description">{{coffee.description}}</span>
        </div>

        <div class="CoffeeDrink_price">
            <span>&euro; {{coffee.price}}</span>
            <button class="CoffeeDrink_choose"
                    @click="$emit('add-drink', coffee.id)"
            >
                <i class="fa fa-plus" aria-hidden="true"></i>
            </button>
        </div>
    </li>
</template>

<script>
    export default {
        name: 'CoffeeListItem',
        props: {
            coffee: {
                type: Object,
                required: true
            }
        },
    }
</script>

<style>
    .CoffeeDrink_content  {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin-bottom: 10px;
        margin-left: 10px;
        font-size: 18px;
        border: 1px solid #e2e2e2;
        width: calc((100% / 2) - 20px);
        box-sizing: border-box;
    }

    .CoffeeDrink_iconBox {
        text-align: center;
        background-color: #008376;
    }

    .CoffeeDrink_icon {
      width: auto;
      height: 150px;
    }

    .CoffeeDrink_information {
        display: flex;
        flex-direction: column;
        padding: 20px;
    }

    .CoffeeDrink_name {
        font-size: 20px;
        letter-spacing: 1px;
        margin-bottom: 10px;
    }

    .CoffeeDrink_price {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 20px 20px;
        box-sizing: border-box;
    }

    .CoffeeDrink_choose {
        width: 50px;
        padding: 5px;
        font-size: 18px;
        background-color: rgb(255, 224, 51);
    }
</style>
