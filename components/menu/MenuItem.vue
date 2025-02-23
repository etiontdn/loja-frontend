<script setup>
const props = defineProps({
    to: String,
});
</script>

<template>
    <NuxtLink class="menu-item" :to="to">
        <slot></slot>
    </NuxtLink>
</template>

<style lang="less">
@import "@/assets/less/textos.less";
@import "@/assets/less/colors.less";

.menu-item {
    padding: 0.5rem;
    cursor: pointer;

    text-decoration: none;

    .texto();

    &:hover {
        background-color: @color-background-dark;

        color: @color-white;
    }
}
</style>
