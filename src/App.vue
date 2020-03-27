<template>
    <div id="app">
        <Header></Header>
        <section class="row">
            <CoffeeList v-bind:coffeeDrinks="coffeeDrinks"
                        @selected-drink="selectedDrink"
            />
            <Basket v-bind:drinksInBasket="drinksInBasket"
                    @delete-item="deleteItem"
            />
        </section>
        <Footer></Footer>
    </div>
</template>

<script>
    import CoffeeList from '@/components/CoffeeList';
    import Basket from '@/components/Basket';
    import Header from '@/components/Header';
    import Footer from '@/components/Footer';

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
            selectedDrink(drink) {
                this.drinksInBasket.push(drink);
            },

            deleteItem(id) {
                this.drinksInBasket = this.drinksInBasket.filter(t => t.id !== id);
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
