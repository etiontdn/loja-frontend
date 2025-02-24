<script setup>
const props = defineProps(["nome", "label", "placeholder", "regex"])
const model = defineModel()

const validation = computed(() => {
    const regex = new RegExp(props.regex);
    return regex.test(model.value);
});

</script>

<template>
    <div class="checkout-input">
        <label class="label" :for="nome">{{ label }}</label>
        <input v-model="model" required class="input" type="text" :name="nome" :id="nome" :placeholder="placeholder">
        <div v-if="!validation && model != ''" class="erro">Campo inválido: tente colocar no formato do exemplo</div>
    </div>
</template>

<style lang="less">
@import "@/assets/less/textos.less";
@import "@/assets/less/colors.less";

.erro {
    .texto();
    color: @color-red;
    font-size: 1rem;
}

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