<template>
  <div class="container max-auto p-5">
    <List v-for="(user, index) in users" 
  :key="user.id" 
  :user="user"
  :index="index"
 @deleteUser="removeUser"/>
  </div>
</template>


<script setup>
import { reactive, ref} from 'vue'
import List from './components/List.vue';

const removeUser = (index) => {
  users.splice(index, 1)
}


const storedUsers = JSON.parse(localStorage.getItem('users')) || defaultUsers

const users = reactive(storedUsers)

// Watch and save to localStorage when users change
watch(
  () => users,
  (newUsers) => {
    localStorage.setItem('users', JSON.stringify(newUsers))
  },
  { deep: true }
)

const defaultUsers = reactive ([
  { id: 1, name: "John Doe", age: 30, position: "Software Engineer" },
  { id: 2, name: "Jane Smith", age: 25, position: "Product Manager" },
  { id: 3, name: "Alice Johnson", age: 28, position: "UX Designer" },
  { id: 4, name: "Bob Brown", age: 35, position: "Data Scientist" },
]);
</script>
