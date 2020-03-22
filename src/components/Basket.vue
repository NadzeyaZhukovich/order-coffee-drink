<template>
    <section class="Basket_content">
        <h2 class="Basket_title">Oder coffee drinks</h2>
        <div class="Basket_cost">
            <span>Total cost:</span>
            <span>&euro; 80</span>
        </div>
        <BasketList></BasketList>
        <div class="Basket_order">
            <button class="Basket_order--btn">Order</button>
        </div>
    </section>
</template>

<script>
    import BasketList from '@/components/BasketList';
    export default {
        name: 'Basket',
        components: {
            BasketList,
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
