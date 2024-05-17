<template>


    <p class="text-center mt-2 text-blue-600 font-bold mt-3 ">Barang</p>

<nuxt-link to="/barang/create/"><button type="button" class="text-white bg-blue-700 m-9 hover:bg-blue-800 focus:outline-none focus:ring-4 focus:ring-blue-300 font-medium rounded-full text-sm px-5 py-2.5 text-center me-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Tambah</button></nuxt-link>
    <center>
        <div class="relative overflow-x-auto items-center">
            <table class="w-full  text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400 text-center">
                <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                    <tr>
                        <th scope="col" class="px-6 py-3">
                            NO
                        </th>


                        <th scope="col" class="px-6 py-3">
                            Nama Barang
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Harga
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Jumlah
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Action
                        </th>
                    </tr>
                </thead>
                <tbody v-for="row in Gudang">

                    <tr class="bg-white gap-3 dark:bg-gray-100">
                        <th scope="row" class="px-2 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-black">
                            {{ no++ }}
                        </th>
                        <td class="px-6 py-4 text-black">
                            {{ row.nama_barang }}
                        </td>
                        <td class="px-6 py-4 text-black">
                            {{ row.harga }}
                        </td>
                        <td class="px-6 py-4 text-black">
                            {{ row.jumlah }}
                        </td>
                        <td>
                           <div class="gap-2">
                            <nuxt-link to="/barang/edit">
                            <button
                                    class="bg-green-500 hover:bg-green-700 text-white font-bold py-1 px-2 rounded">
                                    Update
                                </button>
                            </nuxt-link>
                            <nuxt-link to="/"> <button
                                    class="bg-red-500 hover:bg-red-700 text-white font-bold py-1 px-4 rounded">
                                    Delete
                                </button></nuxt-link>

                            <nuxt-link to="/"> <button
                                    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-1 px-4 rounded">
                                    Show
                                </button></nuxt-link>
                           </div>
                        </td>

                    </tr>

                </tbody>
            </table>
        </div>
    </center>


</template>

<script setup>
let no = 1;
const { data: Gudang } = await useFetch('https://664307293c01a059ea212f61.mockapi.io/api/v1/barang')
</script>