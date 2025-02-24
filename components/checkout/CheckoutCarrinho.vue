<script setup>
import { faker } from "@faker-js/faker";

function gerarProdutoSingle() {
    return {
        img: faker.image.urlLoremFlickr({
            category: "cat",
            height: 400,
            width: 300,
        }),
        nome: faker.commerce.productName(),
        preco: faker.commerce.price({
            dec: 2,
            min: 10,
            max: 200,
        }),
    };
}

const produto = ref(null);
produto.value = gerarProdutoSingle();
</script>
<template>
    <div class="carrinho">
        <h2 class="titulo">Sua sacola</h2>
        <CheckoutCarrinhoProduto v-if="produto" v-bind="produto"></CheckoutCarrinhoProduto>
    </div>
</template>
<style lang="less">
@import "@/assets/less/colors.less";
.carrinho {
    padding: 1rem;
    margin: 2rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    max-height: 25rem;
    background-color: @color-background-light;
}
</style>