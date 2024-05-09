<template>
    <nav
  class="flex-no-wrap relative flex w-full items-center justify-between bg-zinc-50 py-2 shadow-dark-mild dark:bg-neutral-700 flex-wrap justify-start py-4">
  <div class="flex w-full flex-wrap items-center justify-between px-3">

    <div
      class="relative flex items-center"
      id="navbarSupportedContent1"
      data-twe-collapse-item>
      <!-- Left navigation links -->
      <ul
        class="list-style-none me-auto flex ps-0 md:flex-row"
        data-twe-navbar-nav-ref>
        <li class="mb-4 mb-0 pe-2" data-twe-nav-item-ref>
          <!-- Dashboard link -->
          <router-link
            class="text-black/60 transition duration-200 hover:text-black/80 hover:ease-in-out focus:text-black/80 active:text-black/80 motion-reduce:transition-none dark:text-white/60 dark:hover:text-white/80 dark:focus:text-white/80 dark:active:text-white/80 px-2"
            to="/"
            data-twe-nav-link-ref
            >Home</router-link>
        </li>
        <!-- Team link -->
        <li class="mb-4 mb-0 pe-2" data-twe-nav-item-ref>
          <router-link
            class="text-black/60 transition duration-200 hover:text-black/80 hover:ease-in-out focus:text-black/80 active:text-black/80 motion-reduce:transition-none dark:text-white/60 dark:hover:text-white/80 dark:focus:text-white/80 dark:active:text-white/80 px-2"
            to="/products"
            data-twe-nav-link-ref
            >Products</router-link>
        </li>
        <!-- Projects link -->
        <li class="mb-4 mb-0 pe-2" data-twe-nav-item-ref>
          <router-link
            class="text-black/60 transition duration-200 hover:text-black/80 hover:ease-in-out focus:text-black/80 active:text-black/80 motion-reduce:transition-none dark:text-white/60 dark:hover:text-white/80 dark:focus:text-white/80 dark:active:text-white/80 px-2"
            to="/add"
            data-twe-nav-link-ref
            >Add product</router-link>
        </li>
      </ul>
      <!-- Left links -->
    </div>

  </div>
</nav>
</template>

<script>
  export default {
    name: "NavBar"
  }
</script>

<style lang="scss" scoped>

</style>