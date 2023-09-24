<script setup lang="ts">
import BaseCard from './BaseCard.vue';
import { ref } from 'vue-demi';
import BaseIcon from './BaseIcon.vue';

interface BaseMenuProps {
    list: [];
}

const props = defineProps<BaseMenuProps>();
const emits = defineEmits<{
    (e: 'click', item): void;
}>();

const select = ref(false);
const handlerClick = (item) => {
    select.value = item;
    emits('click', item);
};
</script>

<template>
    <div class="menu">
        <BaseCard>
            <div
                class="menu-item"
                v-for="item in props.list"
                :class="{ activeItem: item === select }"
                @click="() => { handlerClick(item); }"
            >
                <div class="title">{{ item }}</div>
                <BaseIcon
                    name="keyboard_arrow_right"
                />
            </div>
        </BaseCard>
    </div>
</template>

<style lang="scss" scoped>

.menu {
    width: 200px;
    top: 0px;
    height: auto;
}

.menu-item {
    position: relative;
    display: flex;
    height: 50px;
    margin-bottom: 15px;
    padding: 5px;
    box-sizing: border-box;
    align-items: center;
    justify-content: space-between;
    transition: 0.3 ease;
    letter-spacing: 1.2px;
    user-select: none;
    cursor: pointer;

    &:hover {
        transform: scale(1.1);

        .arrow {
            transform: scale(1.3);
            animation: 1.5s 0.5s infinite shake ease;
        }

        &::before {
            padding: 0 50%;
        }
    }

    &::before {
        position: absolute;
        content: '';
        height: 1px;
        width: 0px;
        background-color: black;
        bottom: 0px;
        left: 50%;
        transform: translateX(-50%);
        transition: 0.3s ease;
        opacity: 0.3;
    }
}

.title {
    font-size: 18px;
    font-weight: 500;
    transition: 0.3s ease;
}

.arrow {
    transition: 0.3s ease;
}

.activeItem {
    transform: scale(1.1);

    .arrow {
        transform: scale(1.3);
        animation: 1.5s 0.5s infinite shake ease;
    }

    &::before {
        position: absolute;
        content: '';
        height: 1px;
        width: 0px;
        padding: 0 50%;
        background-color: rgb(24, 111, 226);
        bottom: 0px;
        left: 50%;
        transform: translateX(-50%);
        transition: 0.3 ease;
        opacity: 0.7;
    }
}

@keyframes shake {
    0% {
        transform: translateX(0px) scale(1.3);
    }
    50% {
        transform: translateX(3px) scale(1.3);
    }
    100% {
        transform: translateX(0px) scale(1.3);
    }
}

</style>