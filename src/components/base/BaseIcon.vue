<script setup lang="ts">
import { computed } from 'vue';

interface IconProps {
    source?: 'font-awesome' | 'material-symbols';
    name: string;
    fill?: boolean | number | string;
    weight?: number | string;
    grad?: number | string;
    opsz?: number | string;
}

const props = withDefaults(defineProps<IconProps>(), {
    source: 'material-symbols',
    fill: 0,
    weight: 400,
    grad: 0,
    opsz: 40,
});

const iconName = computed(() => {
    if (props.source === 'font-awesome') return 'fa-' + props.name;
    return props.name;
});

const iconStyle = computed(() =>
    `'FILL' ${Number(props.fill)}, 'wght' ${Number(props.weight)},
    'GRAD' ${Number(props.grad)}, 'opsz' ${Number(props.opsz)}`
);

</script>

<template>
    <i
        class="icon"
        :class="{
            fas: props.source === 'font-awesome',
            'material-symbols-rounded': props.source === 'material-symbols',
            [iconName]: iconName,
        }"
        :style="{ 'font-variation-settings': iconStyle }"
    >
        {{ props.source === 'material-symbols' ? iconName : '' }}
    </i>
</template>

<style lang="scss" scoped>

i.icon {
    user-select: none;
    transition: all 0.225s ease-out;
}

.material-symbols-rounded {
    font-family: 'Material Symbols Rounded' !important;
    font-size: inherit;
}

</style>