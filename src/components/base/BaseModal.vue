<script setup lang="ts">

const emits = defineEmits<{ (e: 'clickSelf') }>();
const handlerModalWrapClick = () => {
    emits('clickSelf');
};

</script>

<template>
    <teleport to='.app-container'>
        <transition name="modal" mode="out-in">
            <div class="modal-wrapper" @click.self="handlerModalWrapClick">
                <div class="modal-container">

                    <div class="modal-header">
                        <slot name="header"></slot>
                    </div>

                    <div class="modal-body">
                        <slot name="body"></slot>
                    </div>

                    <div class="modal-footer">
                        <slot name="footer"></slot>
                    </div>
    
                </div>
            </div>
        </transition>    
    </teleport>
</template>

<style lang="scss" scoped>

.modal-wrapper {
    position: fixed;
    z-index: 999;

    display: flex;
    justify-content: center;
    align-items: center;

    width: 100%;
    height: 100%;

    background: rgba(0, 0, 0, 0.3);
}

.modal-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    width: 400px;
    padding: 24px;

    background-color: white;
    border-radius: 8px;
    box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.1);
}

.modal-body {
    flex: 1;
}

</style>