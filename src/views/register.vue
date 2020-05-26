<template>
    <!-- component -->
<body class="font-mono bg-gray-400">
		<!-- Container -->
		<div class="container mx-auto">
			<div class="flex justify-center px-6 my-12">
				<!-- Row -->
				<div class="w-full xl:w-3/4 lg:w-11/12 flex">
					<!-- Col -->
					<div
						class="w-full h-auto bg-gray-400 hidden lg:block lg:w-5/12 bg-cover rounded-l-lg"
						style="background-image: url('https://source.unsplash.com/gvMwYzp-R2U')"
					></div>
					<!-- Col -->
					<div class="w-full lg:w-7/12 bg-white p-5 rounded-lg lg:rounded-l-none">
						<h3 class="pt-4 text-2xl text-center">Create an Account!</h3>
						<form class="px-8 pt-6 pb-8 mb-4 bg-white rounded" id="registerForm" onsubmit="return false;">
							<div class="mb-4">
								<label class="block mb-2 text-sm font-bold text-gray-700" for="name">
									Name
								</label>
								<input
									class="w-full px-3 py-2 mb-3 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
									id="name"
									name="name"
									type="text"
									placeholder="name"
								/>
							</div>
                            <div class='mb-4'>
                                <div class="mb-4 md:flex md:justify-between">
                                    <div class="md:ml-2">
                                        <label class="block mb-2 text-sm font-bold text-gray-700" for="height">
                                            height
                                        </label>
                                        <input
                                            class="w-full px-3 py-2 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
                                            id="height"
                                            name="height"
                                            type="text"
                                            placeholder="height:cm"
                                        />
                                    </div>
                                    <div class="md:ml-2">
                                        <label class="block mb-2 text-sm font-bold text-gray-700" for="weight">
                                            weight
                                        </label>
                                        <input
                                            class="w-full px-3 py-2 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
                                            id="weight"
                                            name="weight"
                                            type="text"
                                            placeholder="weight:kg"
                                        />
                                    </div>
                                </div>
                            </div>
							<div class="mb-4">
								<label class="block mb-2 text-sm font-bold text-gray-700" for="email">
									Email
								</label>
								<input
									class="w-full px-3 py-2 mb-3 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
									id="email"
									name="email"
									type="email"
									placeholder="Email"
								/>
							</div>
							<div class="mb-4 md:flex md:justify-between">
								<div class="mb-4 md:mr-2 md:mb-0">
									<label class="block mb-2 text-sm font-bold text-gray-700" for="password">
										Password
									</label>
									<input
										class="w-full px-3 py-2 mb-3 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
										id="password"
										name="password"
										type="password"
										placeholder="******************"
									/>
								</div>
								<div class="md:ml-2">
									<label class="block mb-2 text-sm font-bold text-gray-700" for="c_password">
										Confirm Password
									</label>
									<input
										class="w-full px-3 py-2 mb-3 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
										id="c_password"
										name="c_password"
										type="password"
										placeholder="******************"
									/>
								</div>
							</div>
                            <div class="mb-4">
                                <label class="block mb-2 text-sm font-bold text-gray-700" for="c_password">
									Working Score
								</label>
                                <div class="relative inline-flex">
                                    <svg class="w-2 h-2 absolute top-0 right-0 m-4 pointer-events-none" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 412 232"><path d="M206 171.144L42.678 7.822c-9.763-9.763-25.592-9.763-35.355 0-9.763 9.764-9.763 25.592 0 35.355l181 181c4.88 4.882 11.279 7.323 17.677 7.323s12.796-2.441 17.678-7.322l181-181c9.763-9.764 9.763-25.592 0-35.355-9.763-9.763-25.592-9.763-35.355 0L206 171.144z" fill="#648299" fill-rule="nonzero"/></svg>
                                    <select id="workingScore" class="border border-gray-300 rounded-full text-gray-600 h-10 pl-5 pr-10 bg-white hover:border-gray-400 focus:outline-none appearance-none">
                                        <option>not working</option>
                                        <option>working</option>
                                        <option>very working</option>
                                    </select>
                                </div>
                            </div>
							<div class="mb-6 text-center">
								<button
									class="w-full px-4 py-2 font-bold text-white bg-blue-500 rounded-full hover:bg-blue-700 focus:outline-none focus:shadow-outline"
									type="button"
                                    @click="register()"
								>
									Register Account
								</button>
							</div>
							<hr class="mb-6 border-t" />
							<div class="text-center">
								<a
									class="inline-block text-sm text-blue-500 align-baseline hover:text-blue-800"
									href="#"
								>
									Forgot Password?
								</a>
							</div>
							<div class="text-center">
								<a
									class="inline-block text-sm text-blue-500 align-baseline hover:text-blue-800"
									href="/login"
								>
									Already have an account? Login!
								</a>
							</div>
						</form>
					</div>
				</div>
			</div>
		</div>
	</body>
</template>
<script>

export default {
    methods: {
        register() {
            var registerForm = document.getElementById('registerForm');
			var registerData = new FormData(registerForm);
            var workingSelect = document.getElementById("workingScore");
            var workingScoreStr = workingSelect.options[workingSelect.selectedIndex].value;
			var workingScore = 0;
			if (workingScoreStr == 'not working') {
				workingScore = 25;
			}else if(workingScoreStr == 'working'){
				workingScore = 30;
			} else {
				workingScore = 40;
			}
			registerData.append('workingScore', workingScore)
			fetch('http://127.0.0.1:5000/register', {
				method: 'POST',
				mode: 'cors',
                body: registerData
            })
            .then((res)=> res.text())
            .then((res) => {
				if (res == 'ok'){
					if(confirm("Go to Login Page?")) {
						location.href = '/login';
					}else {
						alert('fail');
					}
				}
            })
        }
    }
}
</script>