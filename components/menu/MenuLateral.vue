<script setup></script>
<template>
    <div class="menu-lateral">
        <div class="titulo">
            Menu
        </div>
        <MenuItem to="/">Inicio</MenuItem>
        <MenuItem to="/produtos">Produtos</MenuItem>
        <div class="subcategoria">
            <MenuItem to="/produtos/cat">Gatos</MenuItem>
            <MenuItem to="/produtos/dog">Cachorros</MenuItem>
        </div>
        <MenuItem to="/checkout">Checkout</MenuItem>
    </div>
</template>

<style lang="less">
@import "@/assets/less/colors.less";
@import "@/assets/less/media.less";

@keyframes slideInFromLeft {
    0% {
        transform: translateX(-100%);
        opacity: 0;
    }

    100% {
        transform: translateX(0);
        opacity: 1;
    }
}

.subcategoria {
    padding-left: 1rem;
}

.menu-lateral {
    display: none;
    &.active {
        display: flex;
        animation: slideInFromLeft 0.5s ease-in-out;
    }
    flex-direction: column;
    gap: 0.5rem;
    position: absolute;
    top: 6rem;
    left: 0;
    background-color: @color-white;
    padding: 2rem;
    width: 100%;

    @media @md {
        width: 360px;
    }

    height: 80vh;
    border-radius: 0.2rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
</style>
