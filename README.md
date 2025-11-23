# Assignment: Vue.js – Simple To-Do List

## Identitas
- Nama : Fadila Rahmania  
- NIM  : F1D02310048  

---

## Deskripsi Tugas
Pada tugas ini, saya membuat aplikasi **To-Do List** sederhana menggunakan **Vue.js 3** dengan Composition API (```<script setup>```). Aplikasi ini memenuhi semua persyaratan penugasan, berfokus pada konsep dasar reaktivitas, *event handling*, dan *binding*.
### Fitur Utama Aplikasi:
  **1. Tambah Tugas**: Menambahkan tugas baru dari *input* form ke daftar.

  **2. Tampilkan Daftar**: Menampilkan daftar tugas yang ada secara dinamis.

  **3. Hapus Tugas**: Tombol untuk menghapus tugas tertentu dari daftar.

  **4. Kondisi Kosong**: Menampilkan pesan khusus (```"Tidak ada tugas"```) jika daftar kosong.

  **5. Reaktivitas**: Menggunakan ```ref()``` untuk mengelola *state* data

---
## Penjelasan Implementasi Kode (App.vue)
### 1. Reaktivitas dan State Management
Data aplikasi dibuat reaktif menggunakan ```ref()``` dari **Vue**.

```
import { ref } from "vue";

// State
const tasks = ref([]);      // Array reaktif untuk menyimpan daftar tugas.
const newTask = ref("");    // String reaktif, terhubung ke input menggunakan v-model.
```
### 2. Menambah Tugas (```addTask()```)
Fungsi ini terikat pada *event* ```@submit.prevent``` di elemen ```<form>```.

```
function addTask() {
  // 1. Memastikan input tidak kosong atau hanya berisi spasi.
  if (newTask.value.trim() !== "") {
    // 2. Menambahkan nilai input (newTask.value) ke array tasks.
    tasks.value.push(newTask.value);
    // 3. Mereset input agar form bersih.
    newTask.value = "";
  }
}
```
### 3. Menghapus Tugas (```(deleteTask(index)```)
Fungsi ini terikat pada event ```@click``` di tombol "Hapus" pada setiap item daftar.

```
function deleteTask(index) {
  // Menghapus 1 elemen dari array 'tasks' pada posisi 'index' yang spesifik.
  tasks.value.splice(index, 1);
}
```
### 4. Menampilkan Data (```v-for``` dan ```v-if```)
Untuk menampilkan daftar tugas dan mengelola tampilan dinamis, aplikasi menggunakan directives utama Vue.js:

    v-model="newTask": Digunakan pada elemen <input> untuk membuat ikatan dua arah (two-way binding). Hal ini untuk memastikan bahwa state newTask selalu sinkron dengan apa yang diketik pengguna di kolom input.

    v-for="(task, index) in tasks": Digunakan untuk mengulang (iterate) melalui array reaktif tasks dan membuat elemen <li> baru untuk setiap tugas yang ada. Penggunaan :key="index" memastikan Vue dapat melacak setiap elemen secara efisien.

    v-if="tasks.length === 0": Digunakan untuk kontrol kondisi. Pesan "Tidak ada tugas" hanya akan ditampilkan (render) jika panjang array tasks adalah nol, sehingga menghilangkan pesan tersebut secara otomatis ketika tugas pertama ditambahkan.


## Screenshot Hasil Aplikasi
**Screenshot 1: Tampilan awal saat daftar kosong**

<img width="1917" height="1084" alt="Screenshot 2025-11-22 225239" src="https://github.com/user-attachments/assets/bbc5a833-3552-449f-a63d-7c3a9e6c0a58" />

**Screenshot 2: Tampilan saat daftar sudah berisi beberapa tugas**

<img width="1914" height="1077" alt="Screenshot 2025-11-22 225440" src="https://github.com/user-attachments/assets/a107fa92-983b-4b22-a84c-a6ed81565cda" />

**Screenshot 3: Tampilan saat beberapa daftar tugas dihapus**

<img width="1919" height="1075" alt="Screenshot 2025-11-22 225544" src="https://github.com/user-attachments/assets/0519ef31-da29-4aa9-9283-e0bf95feaf23" />


## Screenshot Kode Program

<img width="842" height="1058" alt="gambar" src="https://github.com/user-attachments/assets/7c042a4f-f809-4520-a4d9-083a15b6e4b6" />

<img width="673" height="980" alt="gambar" src="https://github.com/user-attachments/assets/1e77c3b0-7e54-4b05-b3d6-cc8f7fec425a" />

<img width="564" height="964" alt="gambar" src="https://github.com/user-attachments/assets/56b8b38d-ba28-499a-9087-585faa5e7b8b" />










