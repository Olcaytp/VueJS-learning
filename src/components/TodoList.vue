<script setup lang="ts">
import { ref, computed } from 'vue'

interface Todo {
  id: number
  text: string
  completed: boolean
}

const newTodo = ref('')
const todos = ref<Todo[]>([
  { id: 1, text: 'Vue.js Temelleri', completed: true },
  { id: 2, text: 'Component Yapısı', completed: false },
  { id: 3, text: 'Vue Router', completed: false },
])

const addTodo = () => {
  if (!newTodo.value.trim()) return
  
  todos.value.push({
    id: Date.now(),
    text: newTodo.value,
    completed: false
  })
  newTodo.value = ''
}

const removeTodo = (id: number) => {
  todos.value = todos.value.filter(todo => todo.id !== id)
}

const toggleTodo = (id: number) => {
  const todo = todos.value.find(t => t.id === id)
  if (todo) {
    todo.completed = !todo.completed
  }
}

// Hesaplanan özellik örneği
const completedCount = computed(() => {
  return todos.value.filter(todo => todo.completed).length
})
</script>

<template>
  <div class="todo-list">
    <h2>Yapılacaklar Listesi</h2>
    
    <div class="add-todo">
      <input 
        v-model="newTodo"
        @keyup.enter="addTodo"
        placeholder="Yeni görev ekle..."
      >
      <button 
        @click="addTodo"
        :disabled="!newTodo.trim()"
      >
        Ekle
      </button>
    </div>

    <div class="stats">
      Tamamlanan: {{ completedCount }} / {{ todos.length }}
    </div>

    <ul>
      <li 
        v-for="todo in todos" 
        :key="todo.id"
        :class="{ completed: todo.completed }"
      >
        <input 
          type="checkbox"
          :checked="todo.completed"
          @change="toggleTodo(todo.id)"
        >
        <span>{{ todo.text }}</span>
        <button 
          @click.stop="removeTodo(todo.id)"
          class="delete-btn"
        >
          Sil
        </button>
      </li>
    </ul>

    <p v-if="todos.length === 0">
      Henüz görev eklenmemiş
    </p>
  </div>
</template>

<style scoped>
.todo-list {
  max-width: 600px;
  margin: 0 auto;
}

.add-todo {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.add-todo input {
  flex: 1;
  padding: 8px;
  border: 1px solid #374151;
  border-radius: 4px;
  background: #374151;
  color: white;
}

.stats {
  margin-bottom: 20px;
  color: #9ca3af;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px;
  background: #1f2937;
  margin-bottom: 8px;
  border-radius: 4px;
}

li.completed span {
  text-decoration: line-through;
  color: #9ca3af;
}

.delete-btn {
  margin-left: auto;
  background-color: #dc2626;
  padding: 4px 8px;
}
</style>