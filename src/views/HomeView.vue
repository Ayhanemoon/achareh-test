
<template>

  <div class="page-container">
    <div class="page__title">{{ pageTitle }}</div>
    <div class="form__wrapper">
      <div class="form__title">
        {{ formTitle }}
      </div>
      <div class="form-container">
        <div class="form-container__row">
          <div v-for="(inputItem, index) in inputList"
              :key="index"
              :class="[
                'form-container__input',
                inputItem.id === 'address' ? 'form-container__input--fill' : '',
                inputItem.id === 'gender' ? 'form-container__input--full' : ''
              ]">
            <component :is="getInputField(inputItem.type)"
              v-model="inputItem.value"
              :id="inputItem.id"
              :label="inputItem.label"
              :placeholder="inputItem.placeholder"
              :options="inputItem.options"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import TextInput from '@/components/inputs/TextInput/TextInput.vue'
import RadioInput from '@/components/inputs/RadioInput/RadioInput.vue'

const inputList = ref([
  {
    id: 'name',
    type: 'text',
    label: 'نام',
    placeholder: 'مثال : آیهان',
    value: '',
  },
  {
    id: 'family',
    type: 'text',
    label: 'نام خانوادگی',
    placeholder: 'مثال : صمیمی',
    value: '',
  },
  {
    id: 'mobile',
    type: 'text',
    label: 'شماره تلفن همراه',
    placeholder: 'مثال : ۰۹۱۲۱۲۳۴۵۶۷',
    value: '',
  },
  {
    id: 'phone',
    type: 'text',
    label: 'شماره تلفن ثابت (اختیاری)',
    placeholder: 'مثال : ۰۹۱۲۱۲۳۴۵۶۷',
    value: '',
  },
  {
    id: 'address',
    type: 'text',
    label: 'آدرس',
    placeholder: '',
    value: '',
  },
  {
    id: 'gender',
    type: 'radio',
    label: 'جنسیت',
    value: '',
    options: [
      { label: 'مرد', value: 'male' },
      { label: 'زن', value: 'female' },
    ],
  },
])
const pageTitle = 'ثبت آدرس'
const formTitle = 'لطفا مشخصات و آدرس خود را وارد کنید'

const getInputField = (type) => {
  switch (type) {
    case 'text':
      
      return TextInput
    case 'radio':
      return RadioInput

    default:
      break;
  }
}

</script>

<style lang="scss" scoped>
.page-container {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
  gap: 6px;
  width: 100%;
  max-width: 800px;

  &__title {
    font-size: 16px;
    font-weight: 400;
    line-height: 32px;
    letter-spacing: 0px;
  }

  .form {

    &__wrapper {
      width: 100%;
      padding: 22px 48px 30px;
      background: #ffffff;
      border: 1px solid #EDF0F2;
      border-radius: 4px;
      box-shadow: 0 0 16px 0 rgba(0, 0, 0, 0.08);
    }

    &__title {
      font-size: 16px;
      font-weight: 700;
      line-height: 32px;
      letter-spacing: 0px;
      vertical-align: middle;
    }

    &-container {
      display: flex;
      flex-direction: column;
      margin-top: 1rem;

      &__row {
        display: flex;
        flex-wrap: wrap;
        gap: 38px 22px;
        width: 100%;
      }

      &__input {
        flex: 1 1 30%;
        display: flex;
        flex-direction: column;
      }

      &__input--fill {
        flex: 1 1 66%;
      }
      
      &__input--full {
        flex: 1 1 100%;
      }
    }
  }
}
</style>