<script setup>
import { ref, computed } from 'vue'

const emit = defineEmits(['submit'])

const form = ref({
  firstName: '',
  lastName: '',
  email: '',
  phoneNumber: ''
})

const handleSubmit = () => {
  emit('submit', form.value)
  form.value = {
    firstName: '',
    lastName: '',
    email: '',
    phoneNumber: ''
  }
}

const formIsValid = computed(() => {
  return Boolean(form.value.firstName && form.value.phoneNumber)
})
</script>

<template>
  <div class="panel is-success">
    <div class="panel-heading">Add Contact</div>
    <div class="panel-block">
      <form
        @submit.prevent="handleSubmit"
        class="is-flex is-flex-direction-column is-flex-grow-1 mt-3"
      >
        <div class="field">
          <label class="label">First Name</label>
          <div class="control">
            <input
              v-model="form.firstName"
              type="text"
              class="input"
              :class="{ 'is-danger': !form.firstName }"
              placeholder="First Name"
            />
          </div>
        </div>
        <div class="field">
          <label class="label">Last Name</label>
          <div class="control">
            <input v-model="form.lastName" type="text" class="input" placeholder="Last Name" />
          </div>
        </div>
        <div class="field">
          <label class="label">Email</label>
          <div class="control">
            <input v-model="form.email" type="text" class="input" placeholder="Email" />
          </div>
        </div>
        <div class="field">
          <label class="label">Phone Number</label>
          <div class="control">
            <input
              v-model="form.phoneNumber"
              type="text"
              class="input"
              :class="{ 'is-danger': !form.firstName }"
              placeholder="Phone Number"
            />
          </div>
        </div>
        <button
          :disabled="!formIsValid"
          type="submit"
          class="button is-link is-info is-align-self-flex-start mt-3"
        >
          Add Contact
        </button>
      </form>
    </div>
  </div>
</template>

<style scoped></style>
