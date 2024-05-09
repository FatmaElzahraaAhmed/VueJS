<template>
  <div class="container">
    <div class="header">
      <h1>{{ this.id ? "Update" : "Add" }} a product</h1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Et libero nulla eaque error neque ipsa culpa autem, at itaque nostrum!
      </p>
    </div>

    <form @submit.prevent="handleSubmit" class="form">
      <div class="form-group">
        <label for="title">Title</label>
        <div class="input-wrapper">
          <input
            v-model.lazy.trim="title"
            type="text"
            placeholder="Enter title"
          />
        </div>
      </div>

      <div class="form-group">
        <label for="price">Price</label>
        <div class="input-wrapper">
          <input
            v-model.lazy.trim="price"
            type="number"
            placeholder="Enter price"
          />
        </div>
      </div>

      <div class="form-group">
        <label for="qty">Quantity</label>
        <div class="input-wrapper">
          <input
            v-model.lazy.trim="qty"
            type="number"
            placeholder="Enter quantity"
          />
        </div>
      </div>

      <div class="button-container">
        <button type="submit" class="submit-button">
          {{ this.id ? "Update" : "Add" }}
        </button>
      </div>
    </form>
  </div>
</template>

<script>
import ProductsOperations from '../../../public/Mixins/ProductsOperations';

export default {
  data() {
    return {
      product: {},
      id: '',
      title: '',
      price: 0,
      qty: 0,
      productId: 50,
    };
  },
  mixins: [ProductsOperations],
  created() {
    this.id = this.$route.params.id;
    if (this.id) {
      this.GetProductById(this.id).then((res) => {
        this.product = res;
        this.title = res.title;
        this.price = res.price;
        this.qty = res.stock;
      });
    }
  },
  methods: {
    handleSubmit() {
      if (this.id) {
        this.handleUpdateProduct();
      } else {
        this.handleAddProduct();
      }
    },
    async handleAddProduct() {
      try {
        await this.AddProduct(this.title, this.price, this.qty);
      } catch (error) {
        console.error(error);
      }
    },
    async handleUpdateProduct() {
      this.product.title = this.title;
      this.product.stock = this.qty;
      this.product.price = this.price;
      try {
        await this.UpdateProduct(this.product.id, this.product);
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style scoped>
.container {
  margin: auto;
  padding: 16px;
  max-width: 1200px;
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
  margin-top: 16px;
}

.form {
  margin: 32px auto;
  max-width: 600px;
}

.form-group {
  margin-bottom: 16px;
}

.input-wrapper {
  position: relative;
}

.input-wrapper input {
  width: 100%;
  padding: 16px;
  border: 1px solid lightgray;
  border-radius: 8px;
  font-size: 14px;
}

.button-container {
  display: flex;
  justify-content: flex-end;
}

.submit-button {
  background-color: blue;
  color: white;
  padding: 12px 24px;
  font-size: 14px;
  border-radius: 8px;
  border: none;
  cursor: pointer;
}

.submit-button:hover {
  background-color: darkblue;
}
</style>
