<template>

<h1 class="text-lg font-bold mb-5 text-center">Password Generator</h1>


    <div class="w-[500px] max-[510px]:w-[90%] mx-auto text-left">
          
        
        
        <label for="passwordLength" class="text-md text-gray-500 block mb-2"> Password Length:</label>
        <input v-model="passwordLength" @keydown.enter = "generatePassword" type="number" min="4" max="16" id="passwordLength" placeholder="enter a number (4-16) and press 'Enter'" class="block max-[345px]:text-sm shadow-md p-2 w-full border border-gray-300 mb-4">
        
        <label for="uppercase" class="mr-3 text-gray-500">Include Uppercase:</label>
        <input v-model="includeUppercase" type="checkbox" id="uppercase" class="mb-4 "> <br>

        <label for="numbers" class="mr-6 text-gray-500">Include Numbers:</label>
        <input v-model="includeNumbers" type="checkbox" id="numbers" class="mb-4 "> <br>
        
        <label for="symbols" class="mr-7 text-gray-500">Include Symbols:</label>
        <input v-model="includeSymbols" type="checkbox" id="symbols" class=" "> <br>

        <button @click="generatePassword" class="mt-5 p-3 hover:bg-red-800 bg-red-600 text-white font-bold rounded-lg">Generate Password</button>

        <p class="p-2 max-[345px]:text-sm shadow-md border-2 border-green-500 mt-5">Your Password: {{ generatedPassword }} </p>
        
        
    </div>
</template>

<script setup>
import {ref} from 'vue'
const passwordLength = ref()
const includeUppercase = ref(true)
const includeNumbers = ref(true)
const includeSymbols = ref(true)
const generatedPassword = ref('')

const generatePassword = () => {
    const lowerCaseChars = "abcdefghijklmnopqrstuvwxyz"
    const upperCaseChars = includeUppercase.value ?   "ABCDEFGHIJKLMNOPQRSTUVWXYZ" : ''
    const symbols = includeSymbols.value ? "!@#$%^&*" : ''
    const numbers = includeNumbers.value ?  '0123456789' : ''

    const allChars = lowerCaseChars + upperCaseChars + symbols + numbers

    let password = ''

    for (let i = 0; i < passwordLength.value; i++) {
        const randomIndex = Math.floor(Math.random() * allChars.length)
        password += allChars[randomIndex]
        
    }
    generatedPassword.value = password
}

</script>

