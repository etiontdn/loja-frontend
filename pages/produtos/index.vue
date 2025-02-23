<script setup>
async function navigate(option) {
    await navigateTo("/produtos/" + option);
}
</script>

<template>
    <div class="container">
        <ProdutoSeletorCategoria @categoria-selecionada="(option) => navigate(option)"></ProdutoSeletorCategoria>
        <ProdutoGaleria category="cat"></ProdutoGaleria>
    </div>
</template>