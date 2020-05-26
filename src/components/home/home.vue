<template>
    <div class="flex bg-white" style="height:600px;">
        <div class="flex items-center text-center lg:text-left px-8 md:px-12 lg:w-1/2">
            <div>
                <h2 class="text-3xl font-semibold text-gray-800 md:text-4xl">Start Eat <span class="text-indigo-600">Health Meal</span></h2>
                <p class="mt-2 text-sm text-gray-500 md:text-base">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Blanditiis commodi cum cupiditate ducimus, fugit harum id necessitatibus odio quam quasi, quibusdam rem tempora voluptates. Cumque debitis dignissimos id quam vel!</p>
                <div class="flex justify-center lg:justify-start mt-6">
                    <a class="px-4 py-3 bg-gray-900 text-gray-200 text-xs font-semibold rounded hover:bg-gray-800" href="/login">Get Started</a>
                    <a class="mx-4 px-4 py-3 bg-gray-300 text-gray-900 text-xs font-semibold rounded hover:bg-gray-400" href="#">Learn More</a>
                </div>
            </div>
        </div>
        <div class="hidden lg:block lg:w-1/2" style="clip-path:polygon(10% 0, 100% 0%, 100% 100%, 0 100%)">
            <div class="h-full object-cover" style="background-image: url(https://source.unsplash.com/4_jhDO54BYg)">
                <div class="h-full bg-black opacity-25"></div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    created() {
        // document.addEventListener('DOMContentLoaded', function () {

        //     // Get all "navbar-burger" elements
        //     var $navbarBurgers = Array.prototype.slice.call(document.querySelectorAll('.navbar-burger'), 0);
            
        //         // Check if there are any navbar burgers
        //     if ($navbarBurgers.length > 0) {
        //         // Add a click event on each of them
        //         $navbarBurgers.forEach(function ($el) {
        //             $el.addEventListener('click', function () {
            
        //             // Get the "main-nav" element
        //             var $target = document.getElementById('main-nav');
            
        //             // Toggle the class on "main-nav"
        //             $target.classList.toggle('hidden');
            
        //             });
        //         });
        //     }
        // });
    }
}
</script>