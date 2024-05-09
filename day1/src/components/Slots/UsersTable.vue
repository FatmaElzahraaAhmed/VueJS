<template>
  <div class="table-container">
    <table class="data-table">
      <thead class="table-head">
        <tr>
          <th class="header-cell">Name</th>
          <th class="header-cell">Age</th>
          <th class="header-cell">Role</th>
          <th class="action-cell"></th>
        </tr>
      </thead>
  
      <tbody class="table-body">
        <tr v-for="u in users" :key="u.id" class="table-row">
          <td class="table-cell">{{ u.name }}</td>
          <td class="table-cell">{{ u.age }}</td>
          <td class="table-cell">{{ u.role }}</td>
          <td class="table-cell">
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
  props: ['users'],
}
</script>

<style scoped>
.table-container {
  overflow-x: auto;
}

.data-table {
  width: 100%;
  border-collapse: collapse;
  background-color: white;
  font-size: 14px;
}

.table-head {
  text-align: left;
  border-bottom: 2px solid lightgray;
}

.header-cell {
  padding: 8px 16px;
  font-weight: bold;
  color: black;
}

.table-body {
  border-top: 2px solid lightgray;
}

.table-row {
  text-align: center;
}

.table-cell {
  padding: 8px 16px;
  white-space: nowrap;
  color: gray;
}

.action-cell {
  text-align: right;
}

.delete-button {
  background-color: darkred;
  color: white;
  padding: 8px 16px;
  font-size: 10px;
  border-radius: 4px;
  border: none;
  cursor: pointer;
}

.delete-button:hover {
  background-color: darkorange;
}
</style>
