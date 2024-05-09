<template>
  <div class="container">
    <div class="header">
      <h1>Specify your role</h1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Et libero nulla eaque error neque ipsa culpa autem, at itaque nostrum!
      </p>
    </div>

    <form action="#" @submit.prevent="$emit('addUser', name, age, role)" class="form">
      <div class="form-group">
        <label for="name">Name</label>
        <div class="input-wrapper">
          <input
            v-model.lazy.trim="name"
            type="text"
            placeholder="Enter name"
          />
        </div>
      </div>

      <div class="form-group">
        <label for="age">Age</label>
        <div class="input-wrapper">
          <input
            v-model.lazy.trim="age"
            type="number"
            placeholder="Enter age"
          />
        </div>
      </div>

      <div class="form-group">
        <label for="role">Role</label>
        <div class="input-wrapper">
          <select
            v-model="role"
            name="role"
            id="role"
          >
            <option value="">Please select</option>
            <option value="admin">Admin</option>
            <option value="user">User</option>
          </select>
        </div>
      </div>

      <div class="button-group">
        <button type="submit">
          Add
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      age: 0,
      role: "",
    }
  },
  emits: ['addUser'],
  props: ["users", "admins"]
}
</script>

<style scoped>
.container {
  margin: auto;
  padding: 16px;
  max-width: 1000px;
}

.header {
  text-align: center;
}

.header h1 {
  font-size: 24px;
  font-weight: bold;
}

.header p {
  color: gray;
  margin-top: 8px;
}

.form {
  margin: 16px auto;
  max-width: 600px;
}

.form-group {
  margin-bottom: 16px;
}

.input-wrapper {
  position: relative;
}

.input-wrapper input,
.input-wrapper select {
  width: 100%;
  padding: 8px;
  border: 1px solid lightgray;
  border-radius: 4px;
}

.button-group {
  display: flex;
  justify-content: flex-end;
}

.button-group button {
  background-color: blue;
  color: white;
  padding: 8px 16px;
  border-radius: 4px;
  border: none;
  font-size: 14px;
}

.button-group button:hover {
  background-color: darkblue;
}
</style>
