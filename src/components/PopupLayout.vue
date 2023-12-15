<template>
    <div class="fixed inset-0 bg-black bg-opacity-50 flex justify-center items-center">
        <div class="bg-white w-[40%] min-h-[200px] p-4 rounded-lg">
            <div class="flex justify-between items-center font-bold text-lg">
                <slot name="title">
                </slot>
                <div @click="close">
                    <img src="@/assets/images/closebutton.png" alt="close" class="w-5 h-5" />
                </div>
            </div>
            <slot></slot>
        </div>
    </div>
</template>
  

<script setup>
import { defineEmits } from 'vue';

const emits = defineEmits(['close'])

const close = () => emits('close')

</script>

<style scoped></style>