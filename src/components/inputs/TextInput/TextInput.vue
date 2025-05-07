<template>
  <div class="text-input">
    <label :for="id" class="text-input__label">{{ label }}</label>
    <input
      :id="id"
      type="text"
      :placeholder="placeholder"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      class="text-input__input"
    />
  </div>
</template>

<script setup>
const props = defineProps({
  id: {
    type: String,
    required: true,
  },
  label: {
    type: String,
    required: true,
  },
  placeholder: {
    type: String,
    default: '',
  },
  modelValue: {
    type: String,
    default: '',
  },
})

const emit = defineEmits(['update:modelValue'])

</script>

<style lang="scss" scoped>
.text-input {
  display: flex;
  flex-direction: column;
  margin-bottom: 7px;

  &__label {
    height: 22px;
    font-size: 14px;
    font-weight: 500;
    line-height: 100%;
    letter-spacing: 0px;
    color: #37474f
  }

  &__input {
    height: 46px;
    min-width: 222px;
    padding: 0 10px ;
    border: 1px solid #D4D4D4;
    border-radius: 5px;
    font-size: 14px;
    font-weight: 700;
    line-height: 32px;
    letter-spacing: 0px;
    vertical-align: middle;

  }
  
  input:focus-visible {
    outline: 1px solid #00BFA5;
  }
}
</style>