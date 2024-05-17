<!-- EditBarang.vue -->
<template>
  

    <div>
      <h1>Edit Barang</h1>
      <!-- Formulir edit Barang -->
      <form @submit.prevent="editBarang">
        <div>
          <label for="namaBarang">Nama Barang:</label>
          <input type="text" id="namaBarang" v-model="editedBarang.nama_barang" required>
        </div>
  
        <div>
          <label for="hargaBarang">Harga:</label>
          <input type="number" id="hargaBarang" v-model="editedBarang.harga" required>
        </div>
  
        <div>
          <label for="jumlahBarang">Jumlah:</label>
          <input type="number" id="jumlahBarang" v-model="editedBarang.jumlah" required>
        </div>
  
        <button type="submit">Simpan Perubahan</button>
      </form>
    </div>
  </template>
  
  <script setup>
  
//   import { useFetch } from 'vue-fetch';
  
  // Ambil ID barang dari parameter URL
  const idBarang = $route.params.id;
  
  // Ambil data barang dari API berdasarkan ID
  const { data: barang } = await useFetch(`https://664307293c01a059ea212f61.mockapi.io/api/v1/barang/${idBarang}`);
  
  // Data untuk formulir edit
  const editedBarang = reactive(barang);
  
  // Fungsi untuk menyimpan perubahan barang
  const editBarang = async () => {
    try {
      await fetch(`https://664307293c01a059ea212f61.mockapi.io/api/v1/barang/${idBarang}`, {
        method: 'PUT',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(editedBarang),
      });
      console.log('Barang berhasil diperbarui');
      // Redirect ke halaman lain setelah menyimpan perubahan
      $router.push('/barang');
    } catch (error) {
      console.error('Error saat menyimpan perubahan:', error);
    }
  };
  </script>
  