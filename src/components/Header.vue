<template>
    <header class="DesktopHeader_content">
        <div class="DesktopHeader_header">
            <div class="DesktopHeader_logo">
                <a href="#">Coffee Drinks</a>
            </div>
        </div>
    </header>
</template>

<style>
    .DesktopHeader_content {
        width: 100%;
        position: fixed;
        top: 0;
        left: 0;
        z-index: 100;
        box-shadow: 0 0 0 1px rgba(0, 0, 0, 0.1);
        background-color: #ffffff;
    }

    .DesktopHeader_header {
        width: 1200px;
        margin: 0 auto;
        display: flex;
        align-items: center;
        position: relative;
        height: 70px;
    }

    .DesktopHeader_header a {
        text-decoration: none;
        color: #000;
        cursor: pointer;
        font-size: 20px;
    }
</style>
