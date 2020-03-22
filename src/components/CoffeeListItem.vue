<template>
    <li class="CoffeeDrink_content">
        <div class="CoffeeDrink_iconBox">
            <img src="https://api.coffee-drinks.alexzh.com/store/img/196/latte.png" class="CoffeeDrink_icon">
        </div>

        <div class="CoffeeDrink_information">
            <span class="CoffeeDrink_name"><b>Kind of coffee</b></span>
            <span class="CoffeeDrink_description">Ac erat mus lectus dolor habitasse.
                Consequat adipiscing nascetur nunc egestas elit?
                Sapien natoque semper hendrerit eget vulputate magna ut orci torquent.
            </span>
        </div>

        <div class="CoffeeDrink_price">
            <span>&euro; 4</span>
            <button class="CoffeeDrink_choose">
                <i class="fa fa-plus" aria-hidden="true"></i>
            </button>
        </div>
    </li>
</template>

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
