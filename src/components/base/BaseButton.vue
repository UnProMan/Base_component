<script setup lang="ts">

interface BaseButtonProps {
    width?: string;
    height?: string;
    fontSize?: string;
    disabled?: boolean;
}

const props = defineProps<BaseButtonProps>();

</script>

<template>
    <div>
        <button
            class="default__button"
            :disabled="props.disabled"
        >
            <slot></slot>
        </button>
    </div>
</template>

<style lang="scss" scoped>

button {
    width: v-bind(width);
    height: v-bind(height);
    font-size: v-bind(fontSize);
    
    border: 3px solid rgba(var(--orange));
    outline: none;

    display: flex;
    justify-content: center;
    align-items: center;

    padding: 8px 12px;
    cursor: pointer;
    user-select: none;
    border-radius: 8px;
    background-color: white;
    color: black;

    &:hover {
        background: rgba(var(--orange));
        transition: all 0.5s;
    }

    &:active {
        background-color: rgba(var(--orange));
        color: white;
        transition: background 0s;
    }
}

</style>