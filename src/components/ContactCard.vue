<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps(['name', 'phone', 'index'])

const emits = defineEmits(['deleteContact', 'editContact'])

const deleteContact = () => emits('deleteContact', props.index)

const editContact = () => emits('editContact', props.index)



</script>

<template>
    <div class="flex justify-center">
        <div class="flex justify-between border border-[gray] rounded-md w-[80%] px-4 py-2 items-center">
            <div class="flex justify-between items-center w-[60%]">
                <div>
                    <div class="w-8 h-8"><img src="@/assets/images/contact.png" alt="conactimg" /></div>
                </div>
                <div class="flex flex-col w-[70%] gap-y-[1px]">
                    <p class="font-bold">{{props.name}}</p>
                    <p class="font-semibold font-sm">{{props.phone}}</p>
                </div>
            </div>
            <div class="flex flex-col gap-y-2">
                <div class="w-5 h-5">
                    <img src="@/assets/images/edit.png" alt="edit" class="cursor-pointer" @click="editContact" />
                </div>
                <div class="w-5 h-5">
                    <img src="@/assets/images/delete.png" alt="delete" class="cursor-pointer" @click="deleteContact"/>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped></style>