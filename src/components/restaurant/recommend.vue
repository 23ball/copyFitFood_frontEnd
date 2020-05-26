<template>
<div>
    <div class = "m-6">
        <div v-for="recommendMeal in recommendMeals" v-bind:key="recommendMeal" class="flex bg-white rounded">
            <div v-for="dayMeal in recommendMeal" v-bind:key="dayMeal" class="w-1/3 text-center px-6">
                <!-- {{dayMeal}} -->
                <div class="m-6 inline-block">
                    <img :src='dayMeal.image'
                        class=" bg-gray-300 h-64 w-full rounded-lg shadow-md bg-cover bg-center">
                    <div class="w-56 md:w-64 bg-white -mt-10 shadow-lg rounded-lg overflow-hidden">
                        <div class="py-2 text-center font-bold uppercase tracking-wide text-gray-800">
                            <!-- Nike Revolt -->
                            {{dayMeal.foodName}}
                        </div>
                        <div class="flex items-center justify-between py-2 px-3 bg-gray-400">
                            <h1 class="text-gray-800 font-bold ">$129</h1>
                            <button class=" bg-gray-800 text-xs text-white px-2 py-1 font-semibold rounded uppercase hover:bg-gray-700">Add to cart</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
    
</template>
<script>
export default {
    data(){
        return{
            recommendMeals: [],
        }; 
    },
    created : function(){
        fetch('http://127.0.0.1:5000/recommendFood/' + localStorage.getItem('key'), {
                methods:'GET',
                mode: 'cors',
                credentials: "include"
            })
            .then((res)=> res.json())
            .then((res) => {
                // console.log(res);
                this.recommendMeals = res.recommendMeals;
            })
        // var food = new FormData();
        // fetch('http://127.0.0.1:5000/break', {
        //     headers: {'Access-Control-Allow-Origin':'*'},
        //     method: 'GET'
        // })
        // .then((res)=>
        //     // console.log('aaa',res);
        //     res.text())
        // .then((res) => {
        //     console.log(res);
        //     if (res == 'false') {
        //         var fd = prompt('아침 메뉴를 입력');
        //         food.append('food', fd);
        //     }
        //     fetch('http://127.0.0.1:5000/recommendFood', {
        //         headers: {
        //             // 'Content-Type': 'application/json',
        //             // 'Accept': 'application/json'},
        //             'Access-Control-Allow-Origin':'*'},
        //         method: 'POST',
        //         body: food,
        //     })
        //     .then((res)=> res.json())
        //     .then((res) => {
        //         console.log(res);
        //         this.recommends = res.recommend;
        //     })
        // })
    }
};
</script>