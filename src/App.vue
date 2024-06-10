<!-- src/App.vue -->
<template>
  <div id="app">
    <TodoList />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';

export default {
  components: {
    TodoList
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto; /* Mengatur margin secara otomatis */
  width: 80%; /* Mengatur lebar konten */
  border: 2px solid #ccc; /* Menambahkan border dengan ketebalan 2px dan warna #ccc */
  border-radius: 10px; /* Menambahkan sudut border */
  overflow: hidden; /* Mengatur overflow untuk menyembunyikan gambar yang mungkin keluar dari batas */
  /* Menambahkan gambar latar belakang dengan ukuran yang pas dengan border */
  background: url('./background.jpg') no-repeat center center;
  background-size: cover;
}
</style>
