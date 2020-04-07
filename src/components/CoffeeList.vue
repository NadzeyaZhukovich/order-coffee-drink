<template>
    <div class="CoffeeList_content">
        <ul class="CoffeeList_list">
            <CoffeeListItem
                v-for="(coffeeDrink, index) in coffeeDrinks"
                v-bind:coffee="coffeeDrink"
                :key="index"
                @add-drink="addDrink"
            />
        </ul>
    </div>
</template>

<script>
    import CoffeeListItem from "./CoffeeListItem";
    export default {
        name: 'CoffeeList',
        components: {CoffeeListItem},
        props: ['coffeeDrinks'],

        methods: {
            addDrink(id) {
                this.$emit('add-drink', id)
            }
        }
    }
</script>

<style>
    .CoffeeList_content  {
        width: calc(100% - 350px);
    }

    .CoffeeList_list {
        list-style: none;
        padding: 0;
        display: flex;
        flex-wrap: wrap;
    }
</style>
