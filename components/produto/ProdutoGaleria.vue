<script setup>
import { faker } from '@faker-js/faker';

function gerarProdutoSingle() {
    return {
        img: faker.image.urlLoremFlickr({
            category: "product",
            height: 400,
            width: 400
        }),
        nome: faker.commerce.productName(),
        descricao: faker.commerce.productDescription(),
        preco: faker.commerce.price({
            dec: 2,
            min: 10,
            max: 200
        }),
    };
}

const produtos20 = [];
for (let i = 0; i < 20; i++) {
    produtos20.push(gerarProdutoSingle());
}

</script>

<template>
    <div class="produto-galeria">
        <ProdutoSingle v-for="produto in produtos20" :key="produto.nome" v-bind="produto"></ProdutoSingle>
    </div>
</template>

<style lang="less">
@import "@/assets/less/media.less";


</style>