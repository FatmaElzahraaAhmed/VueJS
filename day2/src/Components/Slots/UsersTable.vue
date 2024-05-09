<template>
  <div class="overflow-x-auto">
    <table class="min-w-full divide-y-2 divide-gray-200 bg-white text-sm">
      <thead class="ltr:text-left rtl:text-right">
        <tr>
          <th class="whitespace-nowrap px-4 py-2 font-medium text-gray-900">Name</th>
          <th class="whitespace-nowrap px-4 py-2 font-medium text-gray-900">Age</th>
          <th class="whitespace-nowrap px-4 py-2 font-medium text-gray-900">Role</th>
          <th class="px-4 py-2"></th>
        </tr>
      </thead>
  
      <tbody class="divide-y divide-gray-200">
        <tr v-for="u in users" :key="u.id">
          <td align="center" class="whitespace-nowrap px-4 py-2 font-medium text-gray-900">{{ u.name }}</td>
          <td align="center" class="whitespace-nowrap px-4 py-2 text-gray-700">{{ u.age }}</td>
          <td align="center" class="whitespace-nowrap px-4 py-2 text-gray-700">{{ u.role }}</td>
          <td align="center" class="whitespace-nowrap px-4 py-2">
            <button
              @click="$emit('deleteUser', u.id, u.role)"
              class="inline-block rounded bg-red-800 px-4 py-2 text-xs font-medium text-white hover:bg-indigo-700"
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

<style lang="scss" scoped>

</style>