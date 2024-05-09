<template>
  <div class="table-container">
    <table class="table">
      <thead class="table-header">
        <tr>
          <th class="table-header-cell">Name</th>
          <th class="table-header-cell">Age</th>
          <th class="table-header-cell">Role</th>
          <th class="table-header-cell-action"></th>
        </tr>
      </thead>
  
      <tbody class="table-body">
        <tr v-for="u in admins" :key="u.id">
          <td class="table-cell">{{ u.name }}</td>
          <td class="table-cell">{{ u.age }}</td>
          <td class="table-cell">{{ u.role }}</td>
          <td class="table-cell-action">
            <button
              @click="$emit('deleteUser', u.id, u.role)"
              class="delete-button"
            >
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: ['admins'],
}
</script>

<style scoped>
.table-container {
  overflow-x: auto;
}

.table {
  width: 100%;
  border-collapse: separate;
  border-spacing: 0;
  background-color: white;
  text-align: left;
}

.table-header {
  border-bottom: 2px solid lightgray;
}

.table-header-cell {
  padding: 8px;
  font-weight: bold;
  color: black;
}

.table-body {
  border-top: 2px solid lightgray;
}

.table-cell {
  padding: 8px;
  color: gray;
  text-align: center;
}

.table-cell-action {
  padding: 8px;
  text-align: center;
}

.delete-button {
  background-color: darkred;
  color: white;
  padding: 4px 8px;
  border-radius: 4px;
  border: none;
  font-size: 10px;
}

.delete-button:hover {
  background-color: darkorange;
}
</style>
