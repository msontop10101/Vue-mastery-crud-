<template>
    <PopupLayout @close="closeFromParent">
        <template #title>Add Contact </template>
        <div class="flex w-full justify-center">
            <div class="w-full">
                <div>
                    <form class="flex flex-col gap-y-2">
                        <div class="flex flex-col gap-y-2">
                            <label>Name:</label>
                            <input type="text" class="border w-full h-[48px] rounded-md" v-model="formData.name">
                        </div>
                        <div class="flex flex-col gap-y-2">
                            <label>Phone number:</label>
                            <input type="number" class="border w-full h-[48px] rounded-md" v-model="formData.phone">
                        </div>
                        <div class="flex justify-center " @click="handleSubmit">
                            <AddButton/>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </PopupLayout>
</template>

<script setup>
import PopupLayout from './PopupLayout.vue';
import AddButton from './AddButton.vue'
import { defineEmits, ref } from 'vue';

const emits = defineEmits(['close', 'sendData'])

const closeFromParent = () => emits('close')

const formData = ref({
    name: '',
    phone: ''
})

const handleSubmit = (event) => {
    event.preventDefault();
    emits('sendData', formData.value)
    formData.value.name = ""
    formData.value.phone = ""
}
</script>

<style scoped></style>