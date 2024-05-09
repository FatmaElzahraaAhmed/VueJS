<template>
  <user-form @addUser="addUser"></user-form>
  <div class="mx-auto max-w-screen-xl px-4 sm:px-6 lg:px-8">
    <div class="hidden sm:block">
      <div class="flex gap-6" aria-label="Tabs">
        <button
          @click="flag = 'UsersTable'"
          :class=" flag == 'UsersTable'?'bg-gray-300 text-gray-700': ''"
          class=""
        >
          User
        </button>
  
        <button
          @click="flag = 'AdminTable'"
          :class=" flag == 'AdminTable'?'bg-gray-300 text-gray-700': ''"
          class=""
        >
          Admin
        </button>
      </div>
    </div>
    
    <div class="mb-24">
      <component :is="flag" @deleteUser="deleteUser" :users="users" :admins="admins"/>
    </div>
  </div>
</template>

<script>
import UserForm from "../UserForm.vue";
import AdminTable from '../Slots/AdminTable.vue';
import UsersTable from '../Slots/UsersTable.vue';

export default {
  data() {
    return {
      id: 11,
      flag: "UsersTable",
      users: [
        // Users data
      ],
      admins: [
        // Admins data
      ],
    };
  },
  components: {
    UserForm,
    UsersTable,
    AdminTable,
  },
  methods: {
    isSelected(tab) {
      return this.flag === tab ? 'selected' : '';
    },
    deleteUser(id, role) {
      if (role === "user") {
        this.users = this.users.filter((u) => u.id !== id);
      } else if (role === "admin") {
        this.admins = this.admins.filter((u) => u.id !== id);
      }
    },
    addUser(name, age, role) {
      const newUser = {
        id: this.id++,
        name,
        age,
        role,
      };
      if (role === "admin") {
        this.admins.push(newUser);
      } else if (role === "user") {
        this.users.push(newUser);
      }
    },
  },
};
</script>

<style scoped>
.content-wrapper {
  margin: auto;
  padding: 16px;
  max-width: 1200px;
}

.tab-container {
  display: none;
}

.tabs {
  display: flex;
  gap: 16px;
}

.tab-button {
  padding: 12px 20px;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 500;
  color: gray;
  background-color: white;
  cursor: pointer;
  transition: all 0.2s;
}

.tab-button:hover {
  background-color: lightgray;
  color: darkgray;
}

.selected {
  background-color: lightgray;
  color: darkgray;
}

.table-container {
  margin-bottom: 96px; 
}

button{
  margin: 20px;
  background-color: rgb(65, 65, 158);
  color: white;
  padding: 10px 20px;
  border-radius: 8px;
}
</style>
