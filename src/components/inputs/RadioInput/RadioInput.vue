<template>
  <div class="radio-input">
    <label :for="id" class="radio-input__label">{{ label }}</label>
    <div class="radio-input__options">
      <div
        v-for="option in options"
        :key="option.value"
        class="radio-input__option"
      >
        <input
          type="radio"
          :id="option.value"
          :value="option.value"
          :name="id"
          :checked="modelValue === option.value"
          @change="$emit('update:modelValue', option.value)"
        />
        <label :for="option.value">{{ option.label }}</label>
      </div>
    </div>
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
  options: {
    type: Array,
    required: true,
  },
  modelValue: {
    type: String,
    default: '',
  },
})

const emit = defineEmits(['update:modelValue'])
</script>

<style lang="scss" scoped>
.radio-input {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  min-width: 222px;

  &__label {
    font-size: 14px;
    font-weight: 500;
    line-height: 100%;
    letter-spacing: 0px;
    color: #37474f;
  }

  &__options {
    display: flex;
    margin-right: 100px;
  }

  &__option {
    display: flex;
    align-items: center;
    margin-bottom: 5px;

    input[type='radio'] {
      margin-right: 10px;
      cursor: pointer;
      accent-color: #00BFA5;
      
    }
  }
}
</style>