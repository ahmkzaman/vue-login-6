<script setup>
import { ref } from 'vue';
import WelcomePage from './components/WelcomePage.vue';

const registrationStep = ref('register');
const loggedIn = ref(false);
const username = ref('');

const registerUsername = ref('');
const registerPassword = ref('');

const loginUsername = ref('');
const loginPassword = ref('');

const registerUser = () => {
  // Simulate registration
  registrationStep.value = 'login';
};

const loginUser = () => {
  // Check if login info match registered data
  if (loginUsername.value === registerUsername.value && loginPassword.value === registerPassword.value) {
    loggedIn.value = true;
    username.value = registerUsername.value;
    registrationStep.value = '';
  } else {
    alert('Login failed. Please check your credentials.');
  }
};
</script>

<template>
  <div class="flex items-center justify-center h-screen mt-2 p-4">
    
    
    <div v-if="!loggedIn" class="bg-gradient-to-r from-violet-300 to-fuchsia-300 pt-2 px-8 pb-8 rounded-lg shadow w-1/4">
      
      <template v-if="registrationStep === 'register'">

        <div class="flex justify-center mb-2">
         
          <img src="/src/assets/title1.png" alt="Image" class="w-full h-full rounded-lg " />
        </div>

        <h2 class="text-3xl font-extrabold text-gray-600 mb-4 text-center">Create an Account</h2>

        <form @submit.prevent="registerUser">
       
          <div class="mb-4">
            <label for="username" class="block font-bold mb-1 text-center">Username</label>
            <input v-model="registerUsername" id="username" type="text" class="w-full rounded-md px-3 py-2 border" required />
          </div>
          <div class="mb-4">
            <label for="password" class="block mb-1 font-bold text-center">Password</label>
            <input v-model="registerPassword" id="password" type="password" class="w-full rounded-md px-3 py-2 border" required />
          </div>
          <button type="submit" class="w-full bg-red-500 text-xl text-white py-2 rounded-md hover:bg-red-700">
            Register
          </button>
        </form>
      </template>
      <template v-else-if="registrationStep === 'login'">
        <h2 class="text-2xl font-semibold mb-4 text-gray-600 text-center">User Login</h2>
        <form @submit.prevent="loginUser">
          
          <div class="mb-4">
            <label for="loginUsername" class="block mb-1 font-bold text-center">Username</label>
            <input v-model="loginUsername" id="loginUsername" type="text" class="w-full rounded-md px-3 py-2 border" required />
          </div>
          <div class="mb-4">
            <label for="loginPassword" class="block mb-1 font-bold text-center">Password</label>
            <input v-model="loginPassword" id="loginPassword" type="password" class="w-full rounded-md px-3 py-2 border" required />
          </div>
          <button type="submit" class="w-full bg-blue-500 text-white py-2 rounded-md hover:bg-blue-600 font-bold" >
            Login
          </button>
        </form>
      </template>
    </div>
    <div v-else class="">
      <WelcomePage/>
    </div>
  </div>
  
</template>


<style scoped>

</style>
