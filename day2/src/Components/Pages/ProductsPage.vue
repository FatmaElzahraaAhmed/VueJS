<template>
 <div class="overflow-x-auto">
    <table class="min-w-full divide-y-2 divide-gray-200 bg-white text-sm">
      <thead class="ltr:text-left rtl:text-right">
        <tr>
          <th class="whitespace-nowrap px-4 py-2 font-medium text-gray-900">Title</th>
          <th class="whitespace-nowrap px-4 py-2 font-medium text-gray-900">Description</th>
          <th class="whitespace-nowrap px-4 py-2 font-medium text-gray-900">Price</th>
          <th class="whitespace-nowrap px-4 py-2 font-medium text-gray-900">Stock</th>

          <th class="px-4 py-2"></th>
          <th class="px-4 py-2"></th>

        </tr>
      </thead>
  
      <tbody class="divide-y divide-gray-200">
        <tr v-for="prd in products" :key="prd.id">
          <td  class="whitespace-nowrap px-4 py-2 font-medium text-gray-900">{{ prd.title }}</td>
          <td  class="whitespace-nowrap px-4 py-2 text-gray-700">{{ prd.description }}</td>
          <td  class="whitespace-nowrap px-4 py-2 text-gray-700">{{ prd.price }}</td>
          <td  class="whitespace-nowrap px-4 py-2 text-gray-700">{{ prd.stock }}</td>
          <td  class="whitespace-nowrap px-4 py-2">
            <button
              @click="DeleteProduct(prd.id)"
              class="inline-block rounded bg-red-800 px-4 py-2 text-xs font-medium text-white hover:bg-indigo-700"
            >
              Delete
            </button>
          </td>
          <td  class="whitespace-nowrap px-4 py-2">
            <router-link
              :to="`/products/${prd.id}`"
              class="inline-block rounded bg-blue-800 px-4 py-2 text-xs font-medium text-white hover:bg-indigo-700"
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
import { computed, onMounted } from 'vue';
import { useStore } from 'vuex';
  export default {
   setup() {
    let store = useStore();
    let products = computed(()=> store.state.products);

    onMounted(() => {
      store.dispatch('GetProducts');
    })
    // eslint-disable-next-line no-unused-vars
    let DeleteProduct = (id) => {
      store.dispatch("DeleteProduct", id);
      // products = computed(()=> store.state.products);
    }
    return {
      products, DeleteProduct
    }
   }
  }
</script>

<style lang="scss" scoped>

</style>