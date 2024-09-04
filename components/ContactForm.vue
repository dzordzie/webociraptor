<template>
  <dialog class="contact-dialog" ref="dialogRef">
    <span class="close-button" @click="closeDialog"> ✕ </span>
    <div class="dialog-wrapper">
      <h3 class="form-heading">Just send us a message, and we'll reply</h3>
      <span
        class="submit-message"
        v-show="generalMessage"
        :class="{ success: generalMessage === 'SUCCESS' }"
        >{{ generalMessage }}</span
      >
      <form class="contact-form" @submit.prevent="handleSubmit">
        <FormInput
          label="Name:"
          showAsterisk
          fieldType="input"
          v-model="formData.name"
          :errorMessage="nameMessage"
          class="name"
        />
        <div class="contacts">
          <FormInput
            label="E-mail:"
            showAsterisk
            fieldType="input"
            v-model="formData.email"
            :errorMessage="emailMessage"
            class="email"
          />
          <FormInput
            label="Phone number:"
            fieldType="input"
            inputType="tel"
            v-model="formData.phone"
            class="phone"
          />
        </div>
        <FormInput
          label="Website:"
          fieldType="input"
          inputType="url"
          v-model="formData.web"
          class="web"
        />
        <FormInput
          label="Message: "
          showAsterisk
          fieldType="textarea"
          placeholder="Is there anything you'd like to ask us?"
          v-model="formData.note"
          inputClass="note-area input"
          class="note"
          :errorMessage="noteMessage"
        />
        <GoldButton title="Contact Me" />
      </form>
    </div>
  </dialog>
</template>

<script setup>
const generalMessage = ref('')
const dialogRef = ref(null)
const startValidation = ref(false)

const formData = ref({
  name: '',
  email: '',
  phone: '',
  web: '',
  note: '',
})

const handleSubmit = () => {
  generalMessage.value = ''
  startValidation.value = true

  if (allInputsAreValid()) {
    generalMessage.value = 'SUCCESS'
    startValidation.value = false
    resetForm()
    setTimeout(closeDialog, 2000)
  }
}

const allInputsAreValid = () => {
  return isNameValid.value && isEmailValid.value && isNoteValid.value
}

const isEmailValid = computed(() => {
  return /[a-z0-9][a-z0-9\.\-]+@[a-z0-9]+\.[a-z]+(\.[a-z]+)?/.test(
    formData.value.email
  )
})
const isNameValid = computed(() => {
  return formData.value.name.length >= 3
})
const isNoteValid = computed(() => {
  return formData.value.note.length >= 20
})

const isInputFilled = computed(() => {
  return {
    name: startValidation.value ? formData.value.name.trim().length > 0 : true,
    email: startValidation.value
      ? formData.value.email.trim().length > 0
      : true,
    note: startValidation.value ? formData.value.note.trim().length > 0 : true,
  }
})

const nameMessage = computed(() => {
  if (startValidation.value) {
    if (!isInputFilled.value.name) {
      return 'Fill in all fields marked with *'
    }
    if (!isNameValid.value) {
      return 'Name must be at least three letters long'
    }
  }
  return ''
})

const emailMessage = computed(() => {
  if (startValidation.value) {
    if (!isInputFilled.value.email) {
      return 'Fill in all fields marked with *'
    }
    if (!isEmailValid.value) {
      return 'Email is in the wrong format'
    }
  }
  return ''
})

const noteMessage = computed(() => {
  if (startValidation.value) {
    if (!isInputFilled.value.note) {
      return 'Fill in all fields marked with *'
    }
    if (!isNoteValid.value) {
      return 'Please write a few words'
    }
  }
  return ''
})

const resetForm = () => {
  formData.value = {
    name: '',
    email: '',
    phone: '',
    web: '',
    note: '',
  }
}

const showDialog = () => dialogRef.value?.showModal()
const closeDialog = () => {
  dialogRef.value?.close()
  startValidation.value = false
  resetForm()
  generalMessage.value = ''
}

defineExpose({
  show: showDialog,
  close: closeDialog,
})
</script>

<style scoped>
.contact-dialog {
  margin: 0 auto;
  width: 100%;
  top: 3rem;
  max-width: 35rem;
  min-height: 51rem;
  background-color: rgb(22, 37, 43);
  position: relative;
}

.contact-dialog::backdrop {
  background: rgba(17, 56, 59, 0.95);
}

.dialog-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 29.25rem;
  margin: 0 auto;
}

.close-button {
  position: absolute;
  cursor: pointer;
  font-size: 1.5rem;
  font-weight: 900;
  top: 1.5rem;
  right: 2rem;
}

.close-button:hover {
  color: rgb(251, 127, 118);
}

.submit-message {
  position: absolute;
  top: 10rem;
  font-weight: 800;
  color: red;
}

.success {
  color: #bad455;
}

.form-heading {
  max-width: 23.75rem;
  margin-top: 4.125rem;
  font-size: 1.875rem;
  font-weight: 900;
  line-height: 2.75rem;
  text-align: center;
  align-content: center;
}

.contact-form {
  width: 100%;
  display: flex;
  flex-direction: column;
}

.contacts {
  display: flex;
  gap: 0 1.75rem;
}

.gold-button {
  width: 100%;
  height: 4.5rem;
  font-size: 1.25rem;
  font-weight: 900;
  line-height: 3.25rem;
  text-align: center;
  margin-top: 1.9375rem;
  border-radius: 5px;
}

/* =================== RESPONSIVE ======================= */

@media screen and (max-width: 610px) {
  .contact-dialog {
    width: 87%;
    min-height: clamp(40rem, 120vw, 50.875rem);
  }

  .dialog-wrapper {
    width: 80%;
  }

  .close-button img {
    width: 80%;
    height: auto;
  }

  .form-heading {
    font-size: clamp(1.25rem, 4.9vw, 1.875rem);
    line-height: clamp(1.75rem, 7.2vw, 2.75rem);
  }

  .message {
    top: clamp(7.75rem, 27.5vw, 10rem);
    font-size: clamp(0.6875rem, 2.5vw, 1rem);
  }

  .contacts {
    display: flex;
    gap: 0 4vw;
  }

  .gold-button {
    height: clamp(3.5rem, 11.8vw, 4.5rem);
    font-size: clamp(1.125rem, 3.3vw, 1.25rem);
    margin-top: clamp(1rem, 3.37vw, 1.4375rem);
  }
}
</style>
