<script setup>
const props = defineProps({
    img: String,
    nome: String,
    descricao: String,
    preco: Number,
});

const descricaoComprimida = computed(() => {
    if (props.descricao.length > 159) {
        return props.descricao.substring(0, 159) + "...";
    }
    return props.descricao;
});
</script>
<template>
    <div class="produto-single">
        <figure class="img-container">
            <img class="img" :src="img" alt="" />
        </figure>
        <div class="produto-info">
            <p class="produto-nome">
                {{ nome }}
            </p>
            <p class="produto-descricao">
                {{ descricaoComprimida }}
            </p>
            <p class="produto-preco">R$ {{ preco }}</p>
        </div>
    </div>
</template>
<style lang="less">
@import "@/assets/less/media.less";
@import "@/assets/less/textos.less";

.produto-single {
    display: flex;
    flex-direction: column;

    @media @md {
        flex-direction: row;

        .img-container,
        .produto-info {
            flex: 1 1 0px;
            width: 0;
        }
    }

    padding: 0.5rem;
    gap: 0.5rem;

    flex: 1;
    max-width: 180px;

    @media @md {
        max-width: 460px;
    }

    width: 100%;
}

.img {
    width: 100%;
    height: auto;

    margin: auto;
    aspect-ratio: 1/1;
    object-fit: cover;
}

.produto-info {
    display: flex;
    flex-direction: column;
    gap: 0.2rem;

    .produto-nome {
        .titulo();
    }

    .produto-descricao {
        .texto();
    }

    .produto-preco {
        .subtitulo();
    }
}
</style>
