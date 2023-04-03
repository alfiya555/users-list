<template>
  <div class="users">
    <div class="users__header">
      <div class="users__header-item">Name</div>
      <div class="users__header-item">Email</div>
      <div class="users__header-item">Phone</div>
      <div class="users__header-item">Website</div>
    </div>
    <v-expansion-panels>
      <v-expansion-panel v-for="user in usersList" :key="user.id" class="panel">
        <v-expansion-panel-title class="panel__name">
          <div class="panel__name-item">{{ user.name }}</div>
          <div class="panel__name-item">{{ user.email }}</div>
          <div class="panel__name-item">{{ user.phone }}</div>
          <div class="panel__name-item">{{ user.website }}</div>
        </v-expansion-panel-title>
        <v-expansion-panel-text>
          <div class="panel__info mt-1">
            <UserInfo :user="user" @updateUser="changeValue" />
            <v-btn class="panel__info-btn ml-5" width="40" height="40" color="#FFD300" @click="clickUser(user.id)">v</v-btn>
          </div>
        </v-expansion-panel-text>
      </v-expansion-panel>
    </v-expansion-panels>
  </div>
</template>

<script>
import UserInfo from "@/components/UserInfo";

export default {
  name: 'UsersView',
  components: {
    UserInfo,
  },
  data() {
    return {
      usersList: [],
    }
  },
  methods: {
    changeValue(event) {
      this.usersList = this.usersList.map((item) => {
        if (item.id !== event.id) {
          return item;
        }
        return {
          ...item,
          [event.key]: event.value,
        }
      });
    },
    convertItemFromApi(item) {
      return {
        addressStreet: item.address?.street || "",
        addressSuite: item.address?.suite || "",
        addressCity: item.address?.city || "",
        addressZipcode: item.address?.zipcode || "",
        companyName: item.company?.name || "",
        companyCatchPhrase: item.company?.catchPhrase || "",
        companyBs: item.company?.bs || "",
        name: item.name || "",
        username: item.username || "",
        email: item.email || "",
        phone: item.phone || "",
        website: item.website || "",
      };
    },
    clickUser(id) {
      const user = this.usersList.find((item) => item.id === id);
      alert(JSON.stringify(user));
    }
  },
  created() {
    fetch("https://jsonplaceholder.typicode.com/users").then(async (response) => {
      const data = await response.json();
      this.usersList = (data || []).map(this.convertItemFromApi);
    });
  }
}
</script>

<style scoped lang="scss">
::v-deep {
  & .v-expansion-panel--active {
    margin: 0 !important;
  }

  & .v-expansion-panel--after-active {
    margin: 0 !important;
  }

  & .v-expansion-panel-title__overlay {
    background-color: white;
  }

  & .v-expansion-panel__shadow {
    box-shadow: none;
  }

  & .v-expansion-panel--active > .v-expansion-panel-title, & .v-expansion-panel-title {
    min-height: 40px;
  }

  & .v-expansion-panel-title {
    border: 1px solid #FFD200;
    border-radius: 4px;
  }
}
.users__header {
  display: flex;
  flex-direction: row;
  margin: 0 46px 10px 24px;
  font-weight: 400;
  font-size: 12px;
  line-height: 14px;
  color: #696969;
  opacity: 0.5;

  &-item {
    width: 100%;
  }
}
.panel {
  margin-bottom: 10px !important;

  &__name {
    display: flex;
    flex-direction: row;
  }

  &__name-item {
    width: 100%;
  }

  &__name-icon {
    width: 40px;
  }

  &__info {
    width: 100%;
    display: flex;
    flex-direction: row;
  }

  &__info-btn {
    min-width: 40px !important;
  }
}
</style>
