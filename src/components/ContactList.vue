<script setup>
import ContactListItem from './ContactListItem.vue'

const props = defineProps(['contacts'])
const emit = defineEmits(['delete'])

const handleDelete = (phoneNumber) => {
  emit('delete', phoneNumber)
}
</script>

<template>
  <div class="panel is-success">
    <div class="panel-heading">Contacts</div>
    <div class="panel-block is-flex is-flex-direction-column is-align-items-stretch">
      <div v-for="contact in props.contacts" :key="contact.phoneNumber">
        <ContactListItem :contact="contact" @delete="handleDelete" />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
