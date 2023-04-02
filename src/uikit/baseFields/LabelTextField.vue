<template>
  <div class="text-field-wrapper">
    <div class="text-field-wrapper__label">
      <span>{{ label }}</span>
    </div>
    <div>
      <v-text-field
          class="text-field-wrapper__input"
          hide-details
          :placeholder="placeholder"
          :model-value="modelValue"
          @update:modelValue="changeValue" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'LabelTextField',
  emits: ['update:modelValue'],
  props: {
    label: {
      type: String,
      default: "",
    },
    placeholder: {
      type: String,
    },
    modelValue: String,
  },
  methods: {
    changeValue(title) {
      this.$emit('update:modelValue', title);
    }
  },
}
</script>

<style scoped lang="scss">
.text-field-wrapper {
  display: flex;
  flex-direction: column;

  &__label {
    font-weight: 400;
    font-size: 12px;
    line-height: 14px;
    color: #696969;
    opacity: 0.5;
  }

  &__input {
    border: 1px solid #D9DBDA;
    border-radius: 4px;
  }
}

::v-deep {
  & .v-field__overlay {
    background-color: white !important;
  }

  & .v-field__loader {
    display: none;
  }

  & .v-field__input {
    padding: 10px 17px;
    height: 35px !important;
    min-height: 35px !important;
  }

  & .v-field__outline {
    display: none;
  }

  & .v-input__control {
    height: 35px !important;
    max-height: 35px !important;
  }
}
</style>
