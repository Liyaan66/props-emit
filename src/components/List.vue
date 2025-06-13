<template>
  <ul class="space-y-4 p-4 bg-gray-50 rounded-xl shadow-md">
    <li class="flex items-start justify-between bg-purple-50 p-4 rounded-xl hover:bg-purple-100 transition duration-200">
      <div>
        <p class="text-sm font-semibold text-purple-600">ID: {{ user.id }}</p>
        <p class="text-lg font-medium text-gray-800">{{ user.name }}</p>
        <p class="text-sm text-gray-600">{{ user.age }} years old</p>
      </div>
    </li>
    <button @click="$emit('deleteUser', index)">delete</button>
  </ul>
</template>



<script setup>

defineProps({
  user: {
  type: Object,
  required: true
  },
  index: {
  type: Number,
  required: true
  }


})
</script>