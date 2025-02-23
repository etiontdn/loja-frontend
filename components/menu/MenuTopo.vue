<template>
    <header class="header">
        <MenuButton @toggle-menu="toggleMenu" />
        <MenuLateral :class="{ active: isOpen }"></MenuLateral>
        <div class="logo">Minha Loja</div>
    </header>
</template>

<script setup>
const isOpen = ref(false);

function toggleMenu() {
    isOpen.value = !isOpen.value;
}
</script>

<style lang="less">
@import "@/assets/less/colors.less";
@import "@/assets/less/textos.less";
.header {
    background-color: @color-white;
    padding: 1rem 2rem;
    display: flex;
    justify-content: start;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 100;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    gap: 2rem;

    .logo {
        .titulo();
    }
}
</style>
