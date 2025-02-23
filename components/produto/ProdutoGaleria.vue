<script setup>
import { faker } from "@faker-js/faker";

const props = defineProps({
    category: String,
});

function gerarProdutoSingle() {
    return {
        img: faker.image.urlLoremFlickr({
            category: props.category ? props.category : "cat",
            height: 400,
            width: 300,
        }),
        nome: faker.commerce.productName(),
        descricao: faker.commerce.productDescription(),
        preco: faker.commerce.price({
            dec: 2,
            min: 10,
            max: 200,
        }),
    };
}
const produtos20 = ref([]);
onMounted(() => {
    for (let i = 0; i < 20; i++) {
        produtos20.value.push(gerarProdutoSingle());
    }
});
</script>

<template>
    <div>
        <p class="legenda">Produtos gerados usando fakerjs</p>
        <div class="produto-galeria">
            <ProdutoSingle
                v-for="produto in produtos20"
                :key="produto.nome"
                v-bind="produto"
            ></ProdutoSingle>
        </div>
    </div>
</template>

<style lang="less">
@import "@/assets/less/media.less";
@import "@/assets/less/textos.less";
.legenda {
    .texto();
    text-align: right;
    padding: 1rem;
}

.produto-galeria {
    display: grid;
    gap: 1rem;
    grid-template-columns: 1fr 1fr;
    justify-content: center;
    padding: 1rem;

    @media @md {
        grid-template-columns: 1fr 1fr 1fr;
    }
}
</style>
