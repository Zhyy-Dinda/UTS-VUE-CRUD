<template>
    <div class="m-20">
        <p class="text-center mt-2 text-blue-600 font-bold mt-3">Tambah Barang</p>

        <form @submit.prevent="createBarang" class="mt-4">
            <div class="flex flex-col space-y-4">
                <label for="namaBarang" class="text-sm font-semibold">Nama Barang:</label>
                <input type="text" id="namaBarang" v-model="newBarang.nama_barang" required
                    class="border border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:ring focus:ring-blue-500">

                <label for="hargaBarang" class="text-sm font-semibold">Harga:</label>
                <input type="number" id="hargaBarang" v-model="newBarang.harga" required
                    class="border border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:ring focus:ring-blue-500">

                <label for="jumlahBarang" class="text-sm font-semibold">Jumlah:</label>
                <input type="number" id="jumlahBarang" v-model="newBarang.jumlah" required
                    class="border border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:ring focus:ring-blue-500">

                <button type="submit" class="btn-create bg-blue-500 hover:bg-blue-600 text-white font-semibold py-2 px-4 rounded-md
           focus:outline-none focus:ring focus:ring-blue-500">Tambah</button>
            </div>
        </form>


        <!-- Tampilkan daftar barang -->
        <div class="relative overflow-x-auto items-center">
            <table class="w-6/12 text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400 text-center">
                <!-- Bagian ini diisi oleh data yang diambil dari API -->
            </table>
        </div>
    </div>
</template>
<script setup>
import { ref } from 'vue';
import axios from 'axios';

// Data baru untuk formulir
const newBarang = ref({
    nama_barang: '',
    harga: 0,
    jumlah: 0
});

// Fungsi untuk membuat barang baru
const createBarang = async () => {
    try {
        // Kirim data ke server menggunakan POST request
        const response = await axios.post('https://664307293c01a059ea212f61.mockapi.io/api/v1/barang', newBarang.value);
        console.log('Barang berhasil ditambahkan:', response.data);

        // Bersihkan formulir setelah berhasil menambahkan
        newBarang.value = {
            nama_barang: '',
            harga: 0,
            jumlah: 0
        };

        // Ambil ulang data dari server untuk menampilkan daftar barang yang telah diperbarui
        // Anda bisa menggunakan metode lain untuk menangani ini, seperti menggabungkan response dengan data yang ada.
    } catch (error) {
        console.error('Error saat menambahkan barang:', error);
    }
};
</script>