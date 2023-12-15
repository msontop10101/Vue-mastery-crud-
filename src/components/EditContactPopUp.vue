<template>
    <PopupLayout @close="closeFromParent">
        <template #title>Edit Contact </template>
        <div class="flex w-full justify-center">
            <div class="w-full">
                <div>
                    <form class="flex flex-col gap-y-2">
                        <div class="flex flex-col gap-y-2">
                            <label>Name:</label>
                            <input type="text" class="border w-full h-[48px] rounded-md px-2" v-model="formData.name">
                        </div>
                        <div class="flex flex-col gap-y-2">
                            <label>Phone number:</label>
                            <input type="number" class="border w-full h-[48px] rounded-md px-2" v-model="formData.phone">
                        </div>
                        <div class="flex justify-center " @click="handleSubmit">
                            <AddButton>Save</AddButton>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </PopupLayout>
</template>

<script setup>
import { ref, defineEmits, defineProps } from 'vue';
import PopupLayout from './PopupLayout.vue';
import AddButton from './AddButton.vue';

const emits = defineEmits(['closeFromParent'])

const props = defineProps(['contactData', 'editIndex'])


const closeFromParent = () => emits('closeFromParent')

const formData = ref({
    name: props.contactData[props.editIndex].name,
    phone: props.contactData[props.editIndex].phone
})


const handleSubmit = (event) => {
    event.preventDefault();
    console.log(formData.value)
    // emits('sendData', formData.value)
    formData.value.name = ""
    formData.value.phone = ""
}



</script>

<style scoped></style>