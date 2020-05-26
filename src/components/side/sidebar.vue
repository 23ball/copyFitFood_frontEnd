<template>
    <div>
        <div class="border-4 border-gray-200 md:flex flex-col md:flex-row md:min-h-screen w-full">
            <!-- <div @click.away="open = false" class="flex flex-col w-full md:w-64 text-gray-700 bg-white dark-mode:text-gray-200 dark-mode:bg-gray-800 flex-shrink-0" x-data="{ open: false }"> -->
            <div class="flex flex-col w-full md:w-64 text-gray-700 bg-white dark-mode:text-gray-200 dark-mode:bg-gray-800 flex-shrink-0">
                <!-- <nav :class="{'block': open, 'hidden': !open}" class="flex-grow md:block px-4 pb-4 md:pb-0 md:overflow-y-auto"> -->
                <nav class="flex-grow md:block px-4 pb-4 md:pb-0 md:overflow-y-auto">
                    <a v-for="sideMenu in sideMenus" v-bind:key="sideMenu" class="block px-4 py-2 mt-2 text-sm font-semibold text-gray-900 bg-transparent rounded-lg dark-mode:bg-transparent dark-mode:hover:bg-gray-600 dark-mode:focus:bg-gray-600 dark-mode:focus:text-white dark-mode:hover:text-white dark-mode:text-gray-200 hover:text-gray-900 focus:text-gray-900 hover:bg-gray-200 focus:bg-gray-200 focus:outline-none focus:shadow-outline" href="#">{{sideMenu}}</a>
                </nav>
            </div>
            <component :is="inBody"></component>
        </div>
    </div>
</template>
<script>
import Recommend from '../restaurant/recommend.vue'


export default {
    data: function () {
        return {
            sideMenus : JSON.parse(localStorage.getItem("menu")),
            inBody : Recommend
        }
    },
    components: {
        Recommend
    }
}
</script>