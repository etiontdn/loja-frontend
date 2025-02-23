<script setup>
import cep from 'cep-promise';
const emit = defineEmits(['cep']);
const cepInput = ref("")

const HandleClick = () => {
    if (!ValidateCEP.value) {
        return;
    }
    cep(cepInput.value).then((response) => {
        emit('cep', response);
    });
}

const ValidateCEP = computed(() => {
    const regex = /^[0-9]{8}$/;
    return regex.test(cepInput.value);
});

</script>

<template>
    <div class="input-cep">
        <label class="label" for="cep">CEP</label>
        <div class="button-row">
            <input
                v-model="cepInput"
                class="input"
                type="text"
                id="cep"
                placeholder="00000000"
            />
            <button class="botao">
                <CheckoutInputCEPIcon @click="HandleClick"></CheckoutInputCEPIcon>
            </button>
        </div>
    </div>
</template>

<style lang="less" scoped>
.button-row {
    display: grid;
    grid-template-columns: 1fr 2.8rem;
    gap: 2px;
}
.botao {
    padding: 1px;
    height: 2.8rem;
    width: 2.8rem;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>
