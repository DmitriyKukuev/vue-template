<template>
    <VueFinalModal
        :class="['wrapper', {'wrapper--right': right}]"
        :content-class="['content', {'content--right': right}]"
        overlay-transition="vfm-fade"
        :content-transition="right ? 'vfm-slide-right' : 'vfm-fade'"
        @before-close="beforeClose"
    >
        <div class="flex items-center justify-between gap-10">
            <slot name="title"/>
            <button @click="close" class="ml-auto">
                <XMarkIcon class="w-8 h-8"/>
            </button>
        </div>

        <div>
            <slot/>
        </div>
    </VueFinalModal>
</template>

<script setup lang="ts">
import { VueFinalModal } from 'vue-final-modal';
import {XMarkIcon} from '@heroicons/vue/24/outline';

const props = defineProps<{
    right?: boolean,
    beforeClose?: () => void,
}>();

const emit = defineEmits(['close']);

function close() {
    emit('close');
}
</script>
