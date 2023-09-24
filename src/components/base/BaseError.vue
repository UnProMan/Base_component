<script setup lang="ts">
import BaseIcon from './BaseIcon.vue';

interface BaseErrorProps {
    icon: string;
    title: string;
    subtitle: string;
}

const props = defineProps<BaseErrorProps>();
</script>

<template>
    <div class="error-container">
        <BaseIcon class="icon" :name="props.icon"/>
        <div class="title">{{ props.title }}</div>
        <div class="sub-title">{{ props.subtitle }}</div>
        <slot></slot>
    </div>
</template>

<style lang="scss" scoped>

.error-container {
    margin-top: 270px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.icon {
    font-size: 120px;
    margin-bottom: 16px;
    color: rgba(var(---orange));
}

.title {
    font-size: 40px;
}

.sub-title {
    color: gray;
    font-size: 24px;
}

</style>