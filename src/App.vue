<script setup>
import { ref } from 'vue'
import ContactForm from './components/ContactForm.vue'
import ContactList from './components/ContactList.vue'
import sampleData from './sampleData'

const contacts = ref(sampleData)

const addContact = (contact) => {
  console.log('you submitted a contact')
  contacts.value = [...contacts.value, contact]
}

const deleteContact = (phoneNumber) => {
  contacts.value = contacts.value.filter((contact) => contact.phoneNumber !== phoneNumber)
}
</script>

<template>
  <h1 class="is-size-1 has-text-centered has-text-info">Vue Phonebook</h1>
  <div class="container px-4">
    <div class="columns">
      <div class="column">
        <ContactForm @submit="addContact" />
      </div>
      <div class="column">
        <ContactList :contacts="contacts" @delete="deleteContact" />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
