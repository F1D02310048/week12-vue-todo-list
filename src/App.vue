<template>
  <div class="container">
    <div class="card">
      <h1 class="title">To-Do List</h1>

      <!-- Form Input -->
      <form class="form" @submit.prevent="addTask">
        <input
          v-model="newTask"
          type="text"
          class="input"
          placeholder="Tambah tugas..."
        />
        <button class="btn" type="submit">Tambah</button>
      </form>

      <!-- List Tugas -->
      <ul class="list">
        <li v-if="tasks.length === 0" class="empty">
          Tidak ada tugas
        </li>

        <li
          v-for="(task, index) in tasks"
          :key="index"
          class="item"
        >
          {{ task }}

          <button class="delete" @click="deleteTask(index)">
            Hapus
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

// State
const tasks = ref([]);
const newTask = ref("");

// Tambah Tugas
function addTask() {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
}

// Hapus Tugas
function deleteTask(index) {
  tasks.value.splice(index, 1);
}
</script>

<style>
.container {
  width: 100%;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #f5f6fa;
}

.card {
  width: 420px;
  background: white;
  padding: 30px;
  border-radius: 16px;
  box-shadow: 0px 8px 25px rgba(0, 0, 0, 0.08);
}

.title {
  font-size: 28px;
  font-weight: 700;
  margin-bottom: 20px;
  color: #2c3e50;
}

.form {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.input {
  flex: 1;
  padding: 10px 14px;
  border: 2px solid #dcdde1;
  border-radius: 10px;
  font-size: 15px;
}

.btn {
  padding: 10px 18px;
  background: #3b82f6;
  border: none;
  border-radius: 10px;
  color: white;
  cursor: pointer;
  font-weight: 600;
}

.list {
  padding: 0;
  list-style: none;
}

.empty {
  color: #7f8c8d;
  font-style: italic;
}

.item {
  background: #f1f5f9;
  padding: 12px;
  border-radius: 10px;
  margin-bottom: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.delete {
  background: #ef4444;
  color: white;
  padding: 6px 10px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 12px;
}
</style>



