<template>
    <!-- component -->
<!-- component -->
<div class="w-full">
    <nav class="bg-white shadow-lg">
        <div class="md:flex items-center justify-between py-2 px-8 md:px-12">
            <div class="flex justify-between items-center">
               <div class="text-2xl font-bold text-gray-800 md:text-3xl">
                    <a href="#">Fit Food</a>
               </div>
                <div class="md:hidden">
                    <button type="button" class="block text-gray-800 hover:text-gray-700 focus:text-gray-700 focus:outline-none">
                        <svg class="h-6 w-6 fill-current" viewBox="0 0 24 24">
                            <path class="hidden" d="M16.24 14.83a1 1 0 0 1-1.41 1.41L12 13.41l-2.83 2.83a1 1 0 0 1-1.41-1.41L10.59 12 7.76 9.17a1 1 0 0 1 1.41-1.41L12 10.59l2.83-2.83a1 1 0 0 1 1.41 1.41L13.41 12l2.83 2.83z"/>
                            <path d="M4 5h16a1 1 0 0 1 0 2H4a1 1 0 1 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2z"/>
                        </svg>
                    </button>
                </div>
            </div>
            
            <div class="flex flex-col md:flex-row hidden md:block -mx-2">
                <a href="#" class="text-gray-800 rounded hover:bg-gray-900 hover:text-gray-100 hover:font-medium py-2 px-2 md:mx-2">Home</a>
                <a href="#" class="text-gray-800 rounded hover:bg-gray-900 hover:text-gray-100 hover:font-medium py-2 px-2 md:mx-2">About</a>
                <!-- <a v-on:click="Body = 'Menu'" href="#" class="text-gray-800 rounded hover:bg-gray-900 hover:text-gray-100 hover:font-medium py-2 px-2 md:mx-2">Restaurant</a> -->
                <a v-on:click="showRetaurantMenu()" href="#" class="text-gray-800 rounded hover:bg-gray-900 hover:text-gray-100 hover:font-medium py-2 px-2 md:mx-2">Restaurant</a>
                <a href="#" class="text-gray-800 rounded hover:bg-gray-900 hover:text-gray-100 hover:font-medium py-2 px-2 md:mx-2">Recipe</a>
                <span class="py-2 px-2 md:mx-2 rounded bg-gray-200" hidden id="userInfo">
                    <span class="text-gray-800 rounded py-2 px-2 md:mx-2 md:text-2xl" >user : <span class="font-bold">{{user}}</span></span>
                    <!-- <button type="button" class="text-gray-800 rounded py-2 px-2 md:mx-2" 
                        @clcik="logout()">Logout</button> -->
                    <button type="button" class="text-gray-800 rounded hover:bg-gray-900 hover:text-gray-100 hover:font-medium py-2 px-2 md:mx-2"
                            @click="logout()">
                            Logout
                    </button>
                    <!-- <h1 v-if="check">Yes</h1>
                    <h1 v-else>No</h1> -->
                    <a href="#" class="text-gray-800 rounded hover:bg-gray-900 hover:text-gray-100 hover:font-medium py-2 px-2 md:mx-2">ProFile</a>
                </span>
                <a href="/login" class="text-gray-800 rounded hover:bg-gray-900 hover:text-gray-100 hover:font-medium py-2 px-2 md:mx-2">Login</a>
            </div>
        </div>
    </nav>
    <div id="body">
        <component v-bind:is="Body"></component>
    </div>
</div>
</template>
<script>
import Home from '../components/home/home.vue'
import Menu from '../components/side/sidebar.vue'


export default {
    data: function () {
        return {
            check : true,
            user : '',
            Body : Home,
        }
    },
    components: {
        Home,
        Menu,
    },
    methods: {
        logout() {
            // alert('ok');
            fetch('http://127.0.0.1:5000/logout/'+localStorage.getItem('key'),{
                methods:'GET',
                mode: 'cors',
                credentials: "include"
            }).then((res) => res.text())
            .then((res) => {
                // document.getElementById('userInfo').setAttribute('hidden');
                localStorage.removeItem('key');
				location.href = '/';
            })
        },
        showRetaurantMenu() {
            var arr = ['insert', 'recommend', 'list']
            localStorage.setItem('menu', JSON.stringify(arr));
            this.Body = Menu;
        }
    },
    created() {
        // this.Body = this.Home;
        console.log(localStorage.getItem('key'))
        if (localStorage.getItem('key') != ''){
            // var myHeaders = new Headers();
            // let headers = new Headers();
            // headers.append('Content-Type', 'application/json');
            // headers.append('Accept', 'application/json');
            // headers.append('Authorization', 'Basic ' + base64.encode(username + ":" +  password));
            // headers.append('Origin','http://localhost:8081');
            fetch('http://127.0.0.1:5000/login/check/'+localStorage.getItem('key'), {
                // headers: headers,
                methods:'GET',
                mode: 'cors',
                credentials: "include"
            }).then((res) => res.text())
            .then((res) => {
                console.log(res)
                this.check = true;
                if (res == 'false'){
                    this.check = false;
                }else {
                    console.log(res)
                    this.check = true;
                    this.user = res;
                    document.getElementById('userInfo').removeAttribute('hidden');
                }
            })
        }else {
            this.check = false;
        }
    }
}
</script>