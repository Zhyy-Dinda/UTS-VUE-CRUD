<template>


    <p class="text-center mt-2 text-blue-600 font-bold mt-3 ">Katagori Barang</p>



    <center>
        <div class="relative overflow-x-auto items-center">
            <table class="w-6/12  text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400 text-center">
                <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                    <tr>
                        <th scope="col" class="px-6 py-3">
                            NO
                        </th>

                        <th scope="col" class="px-6 py-3">
                            Category
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Keterangan
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Action
                        </th>
                    </tr>
                </thead>
                <tbody v-for="row in Gudang">

                    <tr class="bg-white dark:bg-gray-100">
                        <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-black">
                            {{ no++ }}
                        </th>
                        <td class="px-6 py-4 text-black">
                            {{ row.kategori }}
                        </td>
                        <td class="px-6 py-4 text-black">
                            {{ row.keterangan }}
                        </td>
                        <td>
                            <nuxt-link to="/barang/edit"><button
                                    class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded">
                                    Update
                                </button>
                            </nuxt-link>
                            <nuxt-link to="/"> <button
                                    class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded">
                                    Delete
                                </button></nuxt-link>

                            <nuxt-link to="/"> <button
                                    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
                                    Show
                                </button></nuxt-link>
                        </td>

                    </tr>

                </tbody>
            </table>
        </div>
    </center>


</template>

<script setup>
let no = 1;
const { data: Gudang } = await useFetch('https://664307293c01a059ea212f61.mockapi.io/api/v1/kategori')
</script>