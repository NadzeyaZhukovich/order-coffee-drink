<template>
    <div class="BasketItem_content">
        <span>
            <span class="BasketItem_product">Latte</span>
            <button class="BasketItem_counter btn ">-</button>
            <span class="BasketItem_quantity">2</span>
            <button class="BasketItem_counter btn">+</button>
        </span>
        <span>
            <span class="BasketItem_cost">&euro; 80</span>
            <button class="BasketItem_delete btn">
                <i class="fa fa-trash" aria-hidden="true"></i>
            </button>
        </span>
    </div>
</template>

<style>
    .BasketItem_content {
        padding: 7px 20px;
        font-size: 18px;
        display: flex;
        justify-content: space-between;
    }

    .BasketItem_product {
        font-size: 18px;
        letter-spacing: 1px;
    }

    .BasketItem_counter {
        width: 20px;
    }

    .BasketItem_quantity {
        margin-left: 10px;
    }

    .BasketItem_cost {
        margin-right: 20px;
    }

    .BasketItem_delete {
        border: none;
    }

    .btn {
        margin-left: 10px;
        background: none;
        cursor: pointer;
        font-size: 18px;
    }
</style>
