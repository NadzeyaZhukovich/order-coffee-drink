<template>
    <div id="app">
        <Header @sort="sort"></Header>
        <section class="row">
            <CoffeeList v-bind:coffeeDrinks="coffeeDrinks"
                        @add-drink="addDrink"/>
            <Basket v-bind:drinksInBasket="drinksInBasket"
                    @delete-item="deleteDrink"
                    @order="order"
                    @delete-drink-item="deleteDrinkItem"
                    @add-drink-item="addDrink"/>
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

    const alphabeticalNameDescComparator = (a, b) => {
        if (a.name > b.name) {
            return -1;
        }
        if (a.name < b.name) {
            return 1;
        }
        return 0;
    };

    const alphabeticalNameAscComparator = (a, b) => {
        if (a.name > b.name) {
            return -1;
        }
        if (a.name < b.name) {
            return 1;
        }
        return 0;
    };

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

            deleteDrink(id) {
                this.drinksInBasket = this.drinksInBasket.filter(element => element.drink.id !== id);
            },

            deleteDrinkItem(id) {
              let product= this.drinksInBasket.find(element => element.drink.id === id);
              if(product.quantity > 1) {
                product.quantity --;
              } else {
                    this.deleteDrink(id);
                }
            },

            order() {
              this.drinksInBasket = this.drinksInBasket.splice(0, this.drinksInBasket.length - 1);
            },

            sort(param) {
                if (param === 'A-Z') {
                    this.coffeeDrinks.sort((a, b) => alphabeticalNameAscComparator(a, b));
                } else {
                    this.coffeeDrinks.sort((a, b) => alphabeticalNameDescComparator(a, b));
                }
            },
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
