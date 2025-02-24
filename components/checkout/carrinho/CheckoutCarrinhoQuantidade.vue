<script setup>
const value = ref(1);

const aumentar = () => {
    value.value++;
};

const diminuir = () => {
    if (value.value > 0) value.value--;
};
</script>

<template>
    <div class="carrinho-quantidade">
        <button @click="diminuir">-</button>
        <input type="number" v-model="value" />
        <button @click="aumentar">+</button>
    </div>
</template>

<style lang="less" scoped>
@import "@/assets/less/textos.less";
@import "@/assets/less/colors.less";

.carrinho-quantidade {
    display: grid;
    grid-template-columns: 3rem 4rem 3rem;
    gap: 0.5rem;
    align-items: center;
}

button {
    .texto();
    background-color: @color-background-dark;
    color: white;
    border: none;
    padding: 0.5rem;
    border-radius: 0.1rem;
    width: 3rem;
    height: 3rem;
    cursor: pointer;
}

input {
    .texto();
    border: 0;
    text-align: center;
    width: 4rem;
    height: 3rem;
    padding: 0.5rem;
}

</style>
