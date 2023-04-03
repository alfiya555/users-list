<template>
  <div class="user-info-wrapper">
    <div v-for="column in userColumns" :key="column.id" class="user-info-wrapper__column">
      <div class="user-info-wrapper__title">
        <span>{{ column.title }}</span>
      </div>
      <div class="user-info-wrapper__fields">
        <div v-for="field in column.fields" :key="field.value" class="user-info-wrapper__fields-item">
          <LabelTextField
              :model-value="user[field.value]"
              @update:modelValue="changeValue($event, user, field)"
              :label="field.title" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import LabelTextField from "@/uikit/baseFields/LabelTextField";

export default {
  name: 'UserInfo',
  emits: ['update:modelValue'],
  props: {
    user: Object,
  },
  components: {
    LabelTextField,
  },
  data() {
    return {
      userColumns: [
        {
          id: 1,
          title: "ADDRESS",
          fields: [
            {
              title: "Street",
              value: "addressStreet"
            },
            {
              title: "Suite",
              value: "addressSuite"
            },
            {
              title: "City",
              value: "addressCity"
            },
            {
              title: "Zipcode",
              value: "addressZipcode"
            },
          ]
        },
        {
          id: 2,
          title: "COMPANY",
          fields: [
            {
              title: "Name",
              value: "companyName"
            },
            {
              title: "CatchPhrase",
              value: "companyCatchPhrase"
            },
            {
              title: "Bs",
              value: "companyBs"
            },
          ]
        },
        {
          id: 3,
          title: "BASIC INFO",
          fields: [
            {
              title: "Name",
              value: "name"
            },
            {
              title: "Username",
              value: "username"
            },
            {
              title: "Email",
              value: "email"
            },
            {
              title: "Phone",
              value: "phone"
            },
            {
              title: "Website",
              value: "website"
            },
          ]
        },
      ],
    }
  },
  methods: {
    changeValue(value, user, field) {
      this.$emit('updateUser', { value, id: user.id, key: field.value });
      this.$emit('update:modelValue', { value, id: user.id, key: field.value });
    }
  },
}
</script>

<style scoped lang="scss">
.user-info-wrapper {
  width: 100%;
  display: flex;
  flex-direction: row;

  &__column {
    width: 100%;
    border: 1px solid #D9DBDA;
  }

  &__title {
    height: 40px;
    padding: 10px 32px;
    border-bottom: 1px solid #D9DBDA;
  }

  &__fields {
    padding: 10px 32px;
  }

  &__fields-item {
    margin-bottom: 10px;
  }
}
</style>
