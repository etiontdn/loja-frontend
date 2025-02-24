<script setup>
import cep from 'cep-promise';
const emit = defineEmits(['cep', 'change']);
const loading = ref(false);
const model = defineModel()
const HandleClick = async () => {
    if (!ValidateCEP.value) {
        return;
    }
    loading.value = true;
    // Apenas para demonstrar o icone de loading
    await new Promise((r) => setTimeout(r, 1000));
    cep(model.value).then((response) => {
        emit('cep', response);
        loading.value = false;
    });
}

const ValidateCEP = computed(() => {
    const regex = /^[0-9]{8}$/;
    return regex.test(model.value);
});

const change = () => {
    emit('change', valor);
}

const valor = ref('');

</script>

<template>
    <div class="input-cep">
        <label class="label" for="cep">CEP</label>
        <div class="button-row">
            <input
                v-model="model"
                class="input"
                type="text"
                id="cep"
                placeholder="00000000"
            />
            <button type="button" class="botao">
                <CheckoutInputCEPIcon v-if="!loading" @change="change" v-model="valor" @click="HandleClick"></CheckoutInputCEPIcon>
                <CheckoutInputLoading v-else></CheckoutInputLoading>
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
