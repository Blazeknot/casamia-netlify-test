<script setup lang="ts">
import { computed, ref } from 'vue'
import { useStore } from 'vuex'

const count = ref(0)
const store = useStore()
const todos = computed(() => store.state.todos)

store.dispatch('loadTodos')
</script>

<template>
  <h1 class="text-primaryPink">Home sweet home</h1>
  <button
    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full"
    type="button"
    @click="count++"
  >
    count is: {{ count }}
  </button>
  <br /><br />
  <ul>
    <li v-for="todo in todos" :key="todo.value">
      {{ todo.value }}
    </li>
  </ul>
  <br />
  <router-link to="/about">Take me to About</router-link>
</template>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
