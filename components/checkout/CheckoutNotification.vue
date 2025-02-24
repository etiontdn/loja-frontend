<template>
    <div :class="['notification', type, 'texto']">
        <slot></slot>
    </div>
</template>

<script setup>
const props = defineProps({
    type: {
        type: String,
        default: "successo",
        validator: (value) => ["successo", "erro"].includes(value),
    },
});
</script>

<style lang="less" scoped>
@import "@/assets/less/colors.less";
@color-green: #2ecc71;

.notification {
    position: fixed;
    bottom: 20px;
    right: 5%;
    padding: 12px 20px;
    border-radius: 8px;
    color: white;
    font-weight: bold;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
    animation: fadeInBottom 0.5s ease;
}

@keyframes fadeInBottom {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.successo {
    background-color: @color-green;
}

.erro {
    background-color: @color-red;
}
</style>
