<script setup lang="ts">
</script>

<template>
    <div class="card-container">
        <slot></slot>
    </div>
</template>

<style lang="scss" scoped>

.card-container {
    background-color: white;
    box-shadow: 0px 4px 12px rgba(125, 125, 125, 0.5);
    border-radius: 16px;
    padding: 28px;
}

</style>