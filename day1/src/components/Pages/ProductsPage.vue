<template>
  <div class="table-container">
    <table class="product-table">
      <thead class="table-header">
        <tr>
          <th class="header-cell">Title</th>
          <th class="header-cell">Description</th>
          <th class="header-cell">Price</th>
          <th class="header-cell">Stock</th>
          <th class="header-cell-action"></th>
          <th class="header-cell-action"></th>
        </tr>
      </thead>
  
      <tbody class="table-body">
        <tr v-for="prd in products" :key="prd.id" class="table-row">
          <td class="table-cell">{{ prd.title }}</td>
          <td class="table-cell">{{ prd.description }}</td>
          <td class="table-cell">{{ prd.price }}</td>
          <td class="table-cell">{{ prd.stock }}</td>
          <td class="table-cell">
            <button
              @click="DeleteProduct(prd.id)"
              class="delete-button"
            >
              Delete
            </button>
          </td>
          <td class="table-cell">
            <router-link
              :to="`/products/${prd.id}`"
              class="update-link"
            >
              Update
            </router-link>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import ProductsOperations from '../../../public/Mixins/ProductsOperations';
  export default {
    mixins:[ProductsOperations],
    created() {
      this.GetProducts();
    }
  }
</script>

<style scoped>
.table-container {
  overflow-x: auto;
}

.product-table {
  width: 100%;
  border-collapse: collapse;
  background-color: white;
  font-size: 14px;
}

.table-header {
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
  border-bottom: 1px solid lightgray;
}

.table-cell {
  padding: 8px 16px;
  white-space: nowrap;
  color: gray;
  text-align: left;
}

.delete-button {
  background-color: darkred;
  color: white;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 12px;
  border: none;
  cursor: pointer;
}

.delete-button:hover {
  background-color: maroon;
}

.update-link {
  background-color: darkblue;
  color: white;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 12px;
  text-decoration: none;
}

.update-link:hover {
  background-color: darkcyan;
}
</style>
