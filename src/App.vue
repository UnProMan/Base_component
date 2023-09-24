<script setup lang="ts">
import BaseButton from '@/components/base/BaseButton.vue';
import BaseIcon from '@/components/base/BaseIcon.vue';
import BaseError from '@/components/base/BaseError.vue';
import BaseCard from '@/components/base/BaseCard.vue';
import BaseModal from '@/components/base/BaseModal.vue';
import BaseInput from '@/components/base/BaseInput.vue';
import { ref } from 'vue';

const isHover = ref<boolean>(false);

const isActive = ref<boolean>(false);

</script>

<template>
    <div class="app-container">

        <div class="main-container">
            <div class="icon">
                <BaseIcon
                    name="Lock"
                    :fill="isHover"
                    @mouseenter="() => (isHover = true)"
                    @mouseleave="() => (isHover = false)"
                />
            </div>
            
            <BaseButton :width="'250px'" @click="isActive = true" >안농</BaseButton>
            
            <BaseInput
                width="300px"
                height="30px"
                caption="캡션"
            />

            <BaseCard>
                <BaseError
                    icon="Lock"
                    title="안녕하세요"
                    subtitle="에러예요"
                >
                </BaseError>
            </BaseCard>
        </div>

    </div>
    
    <BaseModal v-if="isActive" @clickSelf="isActive = false">
        <template #header>
            헤더
        </template>
        <template #body>
            바디입니다.
        </template>
        <template #footer>
            <BaseButton>가즈아</BaseButton>
        </template>
    </BaseModal>
</template>

<style lang="scss">
@import './assets/scss/global.scss';

.icon {
    font-size: 40px;
    font-weight: 800;
}

</style>