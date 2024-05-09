<template>
  
  <div class="mx-auto max-w-screen-xl px-4 py-16 sm:px-6 lg:px-8">
    <div class="mx-auto max-w-lg text-center">
      <h1 class="text-2xl font-bold sm:text-3xl">Specifiy your role</h1>
  
      <p class="mt-4 text-gray-500">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Et libero nulla eaque error neque
        ipsa culpa autem, at itaque nostrum!
      </p>
    </div>
  
    <form action="#" @submit.prevent="$emit('addUser', name, age, role)" class="mx-auto mb-0 mt-8 max-w-md space-y-4">
      <div>
        <label for="name" class="sr-only">Name</label>
  
        <div class="relative">
          <input
            v-model.lazy.trim="name"
            type="text"
            class="w-full rounded-lg border-gray-200 p-4 text-sm shadow-sm"
            placeholder="Enter name"
          />
        </div>
      </div>
  
      <div>
        <label for="age">Age</label>
  
        <div class="relative">
          <input
            v-model.lazy.trim="age"
            type="number"
            class="w-full rounded-lg border-gray-200 p-4  text-sm shadow-sm"
            placeholder="Enter age"
          />
  
        </div>
      </div>

      <div>
        <label for="role" class="block text-sm font-medium text-gray-900"> Role </label>

        <select
          v-model="role"
          name="role"
          id="role"
          class="w-full rounded-lg border-gray-200 p-4 text-sm shadow-sm"
        >
          <option value="">Please select</option>
          <option value="admin">Admin</option>
          <option value="user">User</option>

        </select>
      </div>

  
      <div class="flex items-center justify-between">
        <button
          type="submit"
          class="inline-block rounded-lg bg-blue-500 px-5 py-3 text-sm font-medium text-white"
        >
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
    emits:['addUser'],
    props: ["users", "admins"]
  }
</script>

<style lang="scss" scoped>

</style>