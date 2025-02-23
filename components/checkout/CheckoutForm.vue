<template>
    <div class="checkout-form">
        <h1 class="titulo">Finalização de Pedido</h1>
        <h2 class="subtitulo">Informações de Contato</h2>
        <CheckoutInputTexto
            label="E-mail"
            nome="email"
            placeholder="exemplo@email.com"
        ></CheckoutInputTexto>
        <CheckoutInputTexto
            label="Telefone"
            nome="telefone"
            placeholder="(DDD) 99999-9999"
        ></CheckoutInputTexto>
        <h2 class="subtitulo">Informações de Entrega</h2>
        <CheckoutInputCEP></CheckoutInputCEP>
        <CheckoutInputTexto
            label="Rua"
            nome="rua"
            placeholder=""
        ></CheckoutInputTexto>
        <div class="col-1-2">
            <CheckoutInputTexto
                label="Numero"
                nome="numero"
                placeholder=""
            ></CheckoutInputTexto>
            <CheckoutInputTexto
                label="Bairro"
                nome="bairro"
                placeholder=""
            ></CheckoutInputTexto>
        </div>
        <div class="col-2-1">
            <CheckoutInputTexto
                label="Cidade"
                nome="cidade"
                placeholder=""
            ></CheckoutInputTexto>
            <CheckoutInputTexto
                label="Estado"
                nome="estado"
                placeholder=""
            ></CheckoutInputTexto>
        </div>
        <h2 class="subtitulo">Informações de Pagamento</h2>
        <CheckoutInputTexto
            label="Numero do Cartão"
            nome="num-card"
            placeholder=""
        ></CheckoutInputTexto>
        <CheckoutInputTexto
            label="Titular do Cartão"
            nome="titular-card"
            placeholder=""
        ></CheckoutInputTexto>
        <div class="col-2-1">
            <CheckoutInputTexto
                label="Data de Vencimento"
                nome="data-card"
                placeholder=""
            ></CheckoutInputTexto>
            <CheckoutInputTexto
                label="CVC"
                nome="cvc-card"
                placeholder=""
            ></CheckoutInputTexto>
        </div>
    </div>
</template>
<style lang="less">
.checkout-form {
    padding: 1rem;
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

</style>
