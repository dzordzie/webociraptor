<template>
  <div class="form-section">
    <label>
      {{ label }}
      <span v-if="showAsterisk" class="asterisk">*</span>
    </label>
    <component
      :is="fieldType"
      :type="inputType"
      :placeholder="placeholder"
      :value="modelValue"
      @input="handleInput"
      :class="inputClass"
    />
    <span class="error-message" v-if="errorMessage">{{ errorMessage }}</span>
  </div>
</template>

<script setup>
const props = defineProps({
  type: {
    type: String,
    default: 'text',
  },
  fieldType: {
    type: String,
    default: 'input',
  },
  inputType: {
    type: String,
    default: 'text',
  },
  label: {
    type: String,
    default: '',
  },
  showAsterisk: {
    type: Boolean,
    default: false,
  },
  placeholder: {
    type: String,
    default: '',
  },
  inputClass: {
    type: String,
    default: 'input',
  },
  errorMessage: {
    type: String,
    default: '',
  },
  modelValue: {
    type: String,
    default: '',
  },
})

const emit = defineEmits(['update:modelValue'])

const handleInput = (event) => {
  emit('update:modelValue', event.target.value)
}
</script>

<style scoped>
.form-section {
  display: flex;
  flex-direction: column;
  margin-top: 1.5rem;
  position: relative;
}

.email,
.phone {
  width: 47%;
  max-width: 13.75rem;
}

.input {
  height: 3.4375rem;
  margin-top: 0.8125rem;
  background: var(--backgroudn-semidark);
  border-radius: 5px;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.25rem;
  text-align: left;
  padding: 0 1.375rem 0 1.375rem;
  color: var(--light);
}

.note-area {
  box-sizing: border-box;
  height: 7.5rem;
  padding: 1.375rem;
}

.input::placeholder {
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.25rem;
  text-align: left;
  color: rgba(201, 195, 187, 0.5);
}

.input,
textarea {
  outline: none;
}

.input:focus,
.input:hover,
textarea:focus,
textarea:hover {
  outline: 0.125rem solid var(--dark);
}

.error-message {
  font-size: 12px;
  font-weight: 600;
  color: rgb(252, 155, 148);
  position: absolute;
  bottom: -18px;
}

.form-section label {
  font-size: 1rem;
  font-weight: 900;
  text-align: left;
}

.asterisk {
  color: var(--pinkish);
}

/* =================== RESPONSIVE ======================= */

@media screen and (max-width: 610px) {
  .form-section {
    display: flex;
    flex-direction: column;
    margin-top: clamp(1rem, 4vw, 1.5rem);
  }

  .input {
    height: clamp(2.25rem, 6vw, 3.4375rem);
    margin-top: 0.3125rem;
    font-size: clamp(0.875rem, 2.6vw, 1rem);
    padding: 0 1rem 0 1rem;
  }

  .note-area {
    box-sizing: border-box;
    height: clamp(6.25rem, 20.8vw, 7.9375rem);
    padding: 1rem;
  }

  .input::placeholder {
    font-size: clamp(0.875rem, 2.6vw, 1rem);
  }

  .form-section label {
    font-size: clamp(0.875rem, 2.6vw, 1rem);
  }

  .error-message {
    font-size: clamp(0.5rem, 2vw, 12px);
  }
}
</style>
