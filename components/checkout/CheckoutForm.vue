<script setup>
const email = ref("");
const telefone = ref("");
const rua = ref("");
const numero = ref("");
const bairro = ref("");
const cidade = ref("");
const estado = ref("");
const numCard = ref("");
const titularCard = ref("");
const dataCard = ref("");
const cvcCard = ref("");
const cep = ref("");

const handleAutoCompleteCEP = (response) => {
    rua.value = response.street;
    bairro.value = response.neighborhood;
    cidade.value = response.city;
    estado.value = response.state;
};

const isValid = (value, regex) => {
    if (!regex) return true;
    const reg = new RegExp(regex);
    console.log(value, reg);
    console.log(reg.test(value));
    return reg.test(value);
};

const loading = ref(false);

function validateAll() {
    if (
        !isValid(email.value, "^[a-z0-9.]+@[a-z0-9]+.[a-z]+(.[a-z]+)?$") ||
        !isValid(telefone.value, "^\\([0-9]{2}\\) [0-9]{5}-[0-9]{4}$") ||
        !isValid(
            numCard.value,
            "^[0-9]{4} [0-9]{4} [0-9]{4} [0-9]{1,2}[0-9]{1,2}$"
        ) ||
        !isValid(dataCard.value, "^(0[1-9]|1[0-2])/[0-9]{2}$") ||
        !isValid(cvcCard.value, "^[0-9]{3,4}$") ||
        !isValid(cep.value, "^[0-9]{8}$")
    ) {
        return false;
    }
    return true;
}

const erro = ref(false);
const notificado = ref(false);

async function print() {
    loading.value = true;
    await new Promise((r) => setTimeout(r, 1000));
    if (!validateAll()) {
        erro.value = true;
        loading.value = false;
        return;
    }
    console.log({
        email: email.value,
        telefone: telefone.value,
        cep: cep.value,
        rua: rua.value,
        numero: numero.value,
        bairro: bairro.value,
        cidade: cidade.value,
        estado: estado.value,
        numCard: numCard.value,
        titularCard: titularCard.value,
        dataCard: dataCard.value,
        cvcCard: cvcCard.value,
    });
    loading.value = false;
    erro.value = false;
    notificado.value = true;
    await new Promise((r) => setTimeout(r, 5000));
    notificado.value = false;
}
</script>

<template>
    <form @submit.prevent="print" class="checkout-form">
        <CheckoutNotification v-if="notificado">Sucesso ao Finalizar o Pedido!</CheckoutNotification>
        <h1 class="titulo">Finalização de Pedido</h1>
        <h2 class="subtitulo">Informações de Contato</h2>
        <CheckoutInputTextoValidado
            label="E-mail"
            nome="email"
            placeholder="exemplo@email.com"
            v-model="email"
            regex="^[a-z0-9.]+@[a-z0-9]+\.[a-z]+(\.[a-z]+)?$"
        ></CheckoutInputTextoValidado>
        <CheckoutInputTextoValidado
            label="Telefone"
            nome="telefone"
            placeholder="(DDD) 99999-9999"
            v-model="telefone"
            regex="^\([0-9]{2}\) [0-9]{5}-[0-9]{4}$"
        ></CheckoutInputTextoValidado>
        <h2 class="subtitulo">Informações de Entrega</h2>
        <CheckoutInputCEP
            v-model="cep"
            @cep="handleAutoCompleteCEP"
        ></CheckoutInputCEP>
        <CheckoutInputTexto
            label="Rua"
            nome="rua"
            placeholder="Rua Exemplo"
            v-model="rua"
        ></CheckoutInputTexto>
        <div class="col-1-2">
            <CheckoutInputTexto
                label="Numero"
                nome="numero"
                placeholder="52"
                v-model="numero"
            ></CheckoutInputTexto>
            <CheckoutInputTexto
                label="Bairro"
                nome="bairro"
                placeholder="Bairro Exemplo"
                v-model="bairro"
            ></CheckoutInputTexto>
        </div>
        <div class="col-2-1">
            <CheckoutInputTexto
                label="Cidade"
                nome="cidade"
                placeholder="Rio de Janeiro"
                v-model="cidade"
            ></CheckoutInputTexto>
            <CheckoutInputTexto
                label="Estado"
                nome="estado"
                placeholder="Rio de Janeiro"
                v-model="estado"
            ></CheckoutInputTexto>
        </div>
        <h2 class="subtitulo">Informações de Pagamento</h2>
        <CheckoutInputTextoValidado
            label="Numero do Cartão"
            nome="num-card"
            placeholder="0000 0000 0000 0000"
            v-model="numCard"
            regex="^[0-9]{4} [0-9]{4} [0-9]{4} [0-9]{1,2}[0-9]{1,2}$"
        ></CheckoutInputTextoValidado>
        <CheckoutInputTexto
            label="Titular do Cartão"
            nome="titular-card"
            placeholder="João da Silva"
            v-model="titularCard"
        ></CheckoutInputTexto>
        <div class="col-2-1">
            <CheckoutInputTextoValidado
                label="Data de Vencimento"
                nome="data-card"
                placeholder="02/25"
                v-model="dataCard"
                regex="^(0[1-9]|1[0-2])\/[0-9]{2}$"
            ></CheckoutInputTextoValidado>
            <CheckoutInputTextoValidado
                label="CVC"
                nome="cvc-card"
                placeholder="1111"
                v-model="cvcCard"
                regex="^[0-9]{3,4}$"
            ></CheckoutInputTextoValidado>
        </div>
        <div class="botoes">
            <CheckoutInputBotao
                ><span v-if="!loading">Fechar pedido</span>
                <CheckoutInputLoading v-else></CheckoutInputLoading>
            </CheckoutInputBotao>
            <div v-if="erro" class="erro">
                Algum campo não está preenchido corretamente.
            </div>
        </div>
    </form>
</template>
<style lang="less">
.checkout-form {
    padding: 1rem;
}

.botoes {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
}

.col-1-2 {
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 1rem;
}

.col-2-1 {
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: 1rem;
}

.input-botao {
    margin-top: 1rem;
    flex: 0 0 auto;
}
</style>
