<template>
  <div>
    <nav class="navbar">
      <div class="container">
        <router-link to="/" class="navbar-brand">Navbar</router-link>
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link to="/" class="nav-link">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/products" class="nav-link">Products</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/add" class="nav-link">Add Product</router-link>
          </li>
        </ul>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'NavBar',
};
</script>

<style scoped>
.navbar {
  background-color: #f8f9fa;
  padding: 10px 20px;
}

.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.navbar-brand {
  font-size: 24px;
  font-weight: bold;
  text-decoration: none;
  color: #000;
}

.navbar-nav {
  display: flex;
  list-style: none;
  gap: 20px;
  padding: 0;
  margin: 0;
}

.nav-item {
  padding: 5px;
}           

.nav-link {
  text-decoration: none;
  color: #000;
}

.nav-link:hover {
  color: #0056b3;
}
</style>
