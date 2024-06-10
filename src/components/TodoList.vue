<!-- src/components/TodoList.vue -->
<template>
  <div class="todo-container">
    <h1>Todo List</h1>
    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new task"/>
    <button @click="addTodo">Add</button>
    <ul>
      <li v-for="(todo, index) in todos" :key="index" :class="{ completed: todo.completed }">
        <input type="checkbox" v-model="todo.completed" @change="toggleTodo(index)">
        {{ todo.text }}
        <button @click="removeTodo(index)">Delete</button>
      </li>
    </ul>
    <p>Incomplete tasks: {{ todos.length }}</p> <!-- Menampilkan jumlah tugas yang belum selesai dan total tugas -->
  </div>
</template>

<script>
import { ref } from 'vue';
import { useTodoStore } from '../store';

export default {
  setup() {
    const store = useTodoStore();
    const newTodo = ref('');

    const addTodo = () => {
      if (newTodo.value.trim()) {
        store.addTodo(newTodo.value.trim());
        newTodo.value = '';
      }
    };

    const removeTodo = (index) => {
      store.removeTodo(index);
    };

    const toggleTodo = (index) => {
      store.toggleTodo(index);
    };

    return {
      newTodo,
      todos: store.todos,
      addTodo,
      removeTodo,
      toggleTodo,
      incompleteTodos: store.incompleteTodos // Menggunakan getter incompleteTodos
    };
  }
};
</script>

<style scoped>
.todo-container {
  max-width: 400px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
}

input[type="text"] {
  width: calc(100% - 20px);
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 10px;
  border: none;
  border-radius: 4px;
  background-color: #42b983;
  color: white;
  cursor: pointer;
  margin-right: 5px;
}

button:hover {
  background-color: #3a9c73;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 5px;
  border-bottom: 1px solid #ccc;
}

li.completed {
  text-decoration: line-through;
  color: #888;
}

li button {
  background-color: #e74c3c;
}

li button:hover {
  background-color: #c0392b;
}

p {
  text-align: center;
  font-weight: bold;
}
</style>
