<script setup>
const props = defineProps(["nome", "label", "placeholder"])
</script>

<template>
    <div class="checkout-input">
        <label class="label" :for="nome">{{ label }}</label>
        <input class="input" type="text" :name="nome" :id="nome" :placeholder="placeholder">
    </div>
</template>

<style lang="less">
@import "@/assets/less/textos.less";
@import "@/assets/less/colors.less";

.label {
    .subtitulo();
    font-size: 1.15rem;
    margin-bottom: 0.5rem;
    margin-top: 0.5rem;
}

.checkout-input {
    display: flex;
    flex-direction: column;
}

.input {
    padding: 0.5rem;
    border: 1px solid @text-grey;
    border-radius: 0.2rem;
    .texto();
    font-size: 1.1rem;
}
</style>