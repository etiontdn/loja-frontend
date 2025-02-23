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
            placeholder="Rua Exemplo"
        ></CheckoutInputTexto>
        <div class="col-1-2">
            <CheckoutInputTexto
                label="Numero"
                nome="numero"
                placeholder="52"
            ></CheckoutInputTexto>
            <CheckoutInputTexto
                label="Bairro"
                nome="bairro"
                placeholder="Bairro Exemplo"
            ></CheckoutInputTexto>
        </div>
        <div class="col-2-1">
            <CheckoutInputTexto
                label="Cidade"
                nome="cidade"
                placeholder="Rio de Janeiro"
            ></CheckoutInputTexto>
            <CheckoutInputTexto
                label="Estado"
                nome="estado"
                placeholder="Rio de Janeiro"
            ></CheckoutInputTexto>
        </div>
        <h2 class="subtitulo">Informações de Pagamento</h2>
        <CheckoutInputTexto
            label="Numero do Cartão"
            nome="num-card"
            placeholder="0000 0000 0000 0000"
        ></CheckoutInputTexto>
        <CheckoutInputTexto
            label="Titular do Cartão"
            nome="titular-card"
            placeholder="João da Silva"
        ></CheckoutInputTexto>
        <div class="col-2-1">
            <CheckoutInputTexto
                label="Data de Vencimento"
                nome="data-card"
                placeholder="02/25"
            ></CheckoutInputTexto>
            <CheckoutInputTexto
                label="CVC"
                nome="cvc-card"
                placeholder="1111"
            ></CheckoutInputTexto>
        </div>
        <div class="botoes">
        <CheckoutInputBotao></CheckoutInputBotao>
        </div>
    </div>
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
