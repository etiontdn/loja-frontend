<script setup>
import { ref } from "vue";

const options = ref([
    { nome: "Gatos", valor: "cat" },
    { nome: "Cachorros", valor: "dog" },
]);
const emit = defineEmits(["categoria-selecionada"]);
const active = ref(false);

const selecionarCategoria = (option) => {
    emit("categoria-selecionada", option);
    active.value = false;
};
</script>

<template>
    <div
        @click="active = !active"
        @blur="active = false"
        :class="{ 'select': true, active }"
    >
        <div class="select-label">
            <p>Escolha uma categoria</p>
            <span class="chevron"></span>
        </div>
        <div :class="{ 'select-options': true, active }">
            <div
                @click="
                    () => {
                        selecionarCategoria(option.valor);
                    }
                "
                v-for="option in options"
                :key="option.valor"
                class="select-option"
            >
                {{ option.nome }}
            </div>
        </div>
    </div>
</template>

<style scoped lang="less">
@import "@/assets/less/textos.less";
@import "@/assets/less/colors.less";
.select {
    cursor: pointer;
    border-radius: 0.5rem;
    border: 1px solid @text-grey;
    margin: 1rem;
    position: relative;
    width: 300px;
    .texto();
    background-color: @color-white;

    &.active {
        background-color: @color-background-dark;
        .select-label {
            color: @color-white;
        }
    }
}

.select-label {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.75rem 1rem;
}

.chevron {
    position: relative;
    height: 0.6em;
    width: 0.6em;
    transition: transform 0.3s ease;

    &::before {
        content: "";
        display: block;
        position: absolute;
        width: 0;
        height: 0;
        border-left: 0.5em solid transparent;
        border-right: 0.5em solid transparent;
        border-top: 0.6em solid @text-grey;
    }
}

.select.active .chevron {
    transform: rotate(180deg);
    &::before {
        border-top-color: @color-white;
    }
}

.select-options {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background-color: @color-white;
    border: 1px solid @text-grey;
    border-radius: 0.5rem;
    width: 100%;
    flex-direction: column;
    z-index: 10;
    padding: 0;
    margin-top: 0.25rem;

    &.active {
        display: flex;
    }
}

.select-option {
    padding: 0.75rem 1rem;
    text-align: left;
    cursor: pointer;

    &:hover {
        background-color: @color-background-dark;
        color: @color-white;
    }
}
</style>
