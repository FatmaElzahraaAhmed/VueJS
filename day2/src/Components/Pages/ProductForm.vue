<template>
  <div class="mx-auto max-w-screen-xl px-4 py-16 sm:px-6 lg:px-8">
    <div class="mx-auto max-w-lg text-center">
      <h1 class="text-2xl font-bold sm:text-3xl"> {{ id? "Update" : "Add" }} a product</h1>
  
      <p class="mt-4 text-gray-500">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Et libero nulla eaque error neque
        ipsa culpa autem, at itaque nostrum!
      </p>
    </div>
  
    <form action="#" @submit.prevent="id?HandleUpdateProduct():HandleAddProduct()" class="mx-auto mb-0 mt-8 max-w-md space-y-4">
      <div>
        <label for="title" class="sr-only">Title</label>
  
        <div class="relative">
          <input
            v-model.lazy.trim="title"
            type="text"
            class="w-full rounded-lg border-gray-200 p-4 text-sm shadow-sm"
            placeholder="Enter title"
          />
        </div>
      </div>
  
      <div>
        <label for="price">Price</label>
  
        <div class="relative">
          <input
            v-model.lazy="price"
            type="number"
            class="w-full rounded-lg border-gray-200 p-4  text-sm shadow-sm"
            placeholder="Enter price"
          />
  
        </div>
      </div>

      <div>
        <label for="qty">Quantity</label>
  
        <div class="relative">
          <input
            v-model.lazy="qty"
            type="number"
            class="w-full rounded-lg border-gray-200 p-4  text-sm shadow-sm"
            placeholder="Enter qty"
          />
  
        </div>
      </div>

  
      <div class="flex items-center justify-between">
        <button
          type="submit"
          class="inline-block rounded-lg bg-blue-500 px-5 py-3 text-sm font-medium text-white"
        >
        {{ id? "Update" : "Add" }}
        </button>
      </div>
    </form>
    <div @click="update">hello</div>
  </div>
</template>

<script>
import { computed, onMounted, ref, watch } from "vue";
import { useRoute } from "vue-router";
import { useStore } from "vuex";
  export default {
    setup() {
      const route = useRoute();
      const id = route.params.id;
      const store = useStore();
      const product = computed(()=> store.state.product);
      let title = ref("");
      let price = ref(0);
      let qty = ref(0);
      let productId = ref(50);

      watch(product, (newValue) => {
      title.value = newValue.title;
      price.value = newValue.price;
      qty.value = newValue.stock;
      }, { deep: true });
      
      if (id) {
        onMounted( ()=> {
          store.dispatch('GetProductById', id);
        })
      }
      
      let HandleAddProduct = () => {
          let product = {
            title: title.value,
            price: price.value,
            stock: qty.value
          }
          store.dispatch("AddProduct", product)
      }
      let HandleUpdateProduct = () => {
        product.value.title = title.value;
        product.value.stock = qty.value;
        product.value.price = price.value;
        store.dispatch("UpdateProduct", product.value);
      }
    
      return {
       product, id, title, price, qty, productId, HandleAddProduct, HandleUpdateProduct 
      };
    },
  }
</script>

<style lang="scss" scoped>

</style>