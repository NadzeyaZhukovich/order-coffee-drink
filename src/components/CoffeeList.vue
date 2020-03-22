<template>
    <div class="CoffeeList_content">
        <ul class="CoffeeList_list">
            <CoffeeListItem/>
            <CoffeeListItem/>
            <CoffeeListItem/>
        </ul>
    </div>
</template>

<script>
    import CoffeeListItem from "./CoffeeListItem";
    export default {
        name: 'CoffeeList',
        components: {CoffeeListItem}
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
