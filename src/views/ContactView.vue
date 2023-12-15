<script setup>
import AddButton from '@/components/AddButton.vue';
import AddContactPopUp from '@/components/AddContactPopUp.vue';
import ContactCard from '@/components/ContactCard.vue';
import EditContactPopUp from '@/components/EditContactPopUp.vue';
import { ref } from 'vue'

const toggle = ref(false)
const showEdit = ref(false)
const editIndex = ref(0)

const contactData = ref([
  {name:"ston", phone:'0902929'}
])

const addContact = (formData) => {
  contactData.value.push({ ...formData })
  console.log(contactData.value)
}

const updateAfterDeleted = (selctedIndex) => {
  contactData.value.splice(selctedIndex, 1);
}

const editContact = (selctedIndex) => {
  showEdit.value = true
  editIndex.value = selctedIndex
  console.log(`edit ${selctedIndex} contact`)
}


const handleClose = () => {
  toggle.value = false
}
const handleEditClose = () => {
  showEdit.value = false
}

</script>

<style></style>

<template>
  <Teleport to="#protal-root">
    <div v-show="toggle">
      <AddContactPopUp @close="handleClose" @sendData="addContact" />
    </div>
    <div v-show="showEdit">
      <EditContactPopUp @closeFromParent="handleEditClose" :contactData="contactData" :editIndex="editIndex" />
    </div>
  </Teleport>
  <div class="w-full h-screen flex justify-center items-center">
    <div class="w-[35%] border border-[gray] rounded-md px-3">
      <div class="flex items-center w-full justify-between py-3">
        <p class="font-bold text-lg">--Your Contacts--</p>
        <div class="w-6 h-6 border border-[black] rounded-full overflow-hidden cursor-pointer">
          <img src="@/assets/images/profileicon.png" alt="profileicon" />
        </div>
      </div>
      <div class="py-3 flex flex-col gap-y-2">
        <div v-for="(contact, index) in contactData" :key="index">
          <ContactCard :index="index" :name="contact.name" :phone="contact.phone" @deleteContact="updateAfterDeleted" @editContact="editContact"/>
        </div>
      </div>
      <div class="py-2 flex justify-center w-full">
        <div class="w-[100px]" @click="toggle = !toggle">
          <AddButton />
        </div>
      </div>
    </div>
  </div>
</template>
