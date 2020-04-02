<template>
    <div id="app">
        <Header></Header>
        <section class="row">
            <CoffeeList v-bind:coffeeDrinks="coffeeDrinks"
                        @selected-drink="addDrink"/>
            <Basket v-bind:drinksInBasket="drinksInBasket"
                    @delete-item="deleteItem"
                    @order="order"
                    @delete-product-item="deleteProductItem"
                    @add-product-item="addDrink"/>
        </section>
        <Footer></Footer>
    </div>
</template>

<script>
    import CoffeeList from '@/components/CoffeeList';
    import Basket from '@/components/Basket';
    import Header from '@/components/Header';
    import Footer from '@/components/Footer';
    import BasketProduct from '@/models/basket-product';

    export default {
        name: 'App',
        components: {
            CoffeeList,
            Basket,
            Header,
            Footer,
        },

        data() {
            return {
                coffeeDrinks: [],
                drinksInBasket: [],
            }
        },

        created() {
            fetch('https://order-coffee-drinks.herokuapp.com/api/v1/drinks')
              .then(response => response.json())
              .then(json => {
                  this.coffeeDrinks = json;
              });
        },

        methods: {
            addDrink(id) {
                let product =  this.drinksInBasket.find(element => element.drink.id === id);
                if(product !== undefined) {
                    product.quantity++;
                } else {
                    const drink = this.coffeeDrinks.find(element => element.id === id);
                    this.drinksInBasket.push(new BasketProduct(drink, 1));
                }
            },

            deleteItem(id) {
                this.drinksInBasket = this.drinksInBasket.filter(element => element.drink.id !== id);
            },

            deleteProductItem(id) {
              let product= this.drinksInBasket.find(element => element.drink.id === id);
              if(product.quantity > 1) {
                product.quantity --;
              } else {
                    this.deleteItem(id);
                }
            },

            order() {
              this.drinksInBasket = this.drinksInBasket.splice(0, this.drinksInBasket.length - 1);
            }
        }
    }
</script>

<style>
    .row {
        width: 1200px;
        margin: 70px auto 0;
        display: flex;
        padding-top: 10px;
    }
</style>
