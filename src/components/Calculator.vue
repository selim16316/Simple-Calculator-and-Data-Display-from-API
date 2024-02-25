<script setup>
import { ref, reactive } from 'vue'
const formData = reactive({
    firstValue: 0,
    operator: 1,
    secondValue: 0
})
const result = ref(0);
const calculate = () => {
    if(formData.operator == 1){
        result.value = formData.firstValue + formData.secondValue
    } else if (formData.operator == 2) {
        result.value = formData.firstValue - formData.secondValue
    } else if (formData.operator == 3) {
        result.value = formData.firstValue * formData.secondValue
    } else if (formData.operator == 4) {
        result.value = formData.firstValue / formData.secondValue
    }
}
</script>
<template>
    <section class="max-w-[700px] mt-20 mx-5 md:mx-auto shadow-lg shadow-slate-100 px-5 py-10 border rounded">
        <h2 class="text-center text-2xl font-bold">Simple Calculator</h2>
        <div class="mt-5">
            <form @submit.prevent="calculate()">
            <div class="mx-auto max-w-[400px]">
                <label for="value1st">First Value</label>
                <input v-model="formData.firstValue" id="value1st" type="number" class="border my-2 focus:bg-gray-50 focus:border  text-gray-900 text-sm rounded-lg placeholder-gray-600 focus:placeholder-gray-500 outline-none focus:border-blue-500 p-2.5 text-end w-full" required>
            </div>
            <div class="mx-auto max-w-[400px]">
                <label for="value2nd">Second Value</label>
                <input v-model="formData.secondValue" id="value2nd" type="number" class="border my-2 focus:bg-gray-50 focus:border  text-gray-900 text-sm rounded-lg placeholder-gray-600 focus:placeholder-gray-500 outline-none focus:border-blue-500 p-2.5 text-end w-full" required>
            </div>

            <div class="mx-auto max-w-[400px]">
                <span>Select Operator</span>
                <div class="flex">
                <div class="flex items-center mb-4 mt-2">
                    <input v-model="formData.operator" checked id="operator-1" type="radio" value="1" name="operator" class="operator w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 hidden">
                    <label for="operator-1" class="cursor-pointer bg-gray-300 ms-2 text-lg font-medium text-gray-900 dark:text-gray-300 border px-5 py-3 rounded ml-0">+</label>
                </div>
                <div class="flex items-center mb-4 mt-2">
                    <input v-model="formData.operator"  id="operator-2" type="radio" value="2" name="operator" class="operator w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 hidden">
                    <label for="operator-2" class="cursor-pointer bg-gray-300 ms-2 text-lg font-medium text-gray-900 dark:text-gray-300 border px-5 py-3 rounded">-</label>
                </div>
                <div class="flex items-center mb-4 mt-2">
                    <input v-model="formData.operator"  id="operator-3" type="radio" value="3" name="operator" class="operator w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 hidden">
                    <label for="operator-3" class="bg-gray-300 ms-2 text-lg font-medium text-gray-900 dark:text-gray-300 border px-5 py-3 rounded cursor-pointer">x</label>
                </div>
                <div class="flex items-center mb-4 mt-2">
                    <input v-model="formData.operator"  id="operator-4" type="radio" value="4" name="operator" class="operator w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 hidden">
                    <label for="operator-4" class="bg-gray-300 ms-2 text-lg font-medium text-gray-900 dark:text-gray-300 border px-5 py-3 rounded cursor-pointer">/</label>
                </div>
                
            </div>
            </div>

            <div class="mx-auto max-w-[400px] mt-2">
                <button type="submit" class="focus:outline-none text-white bg-purple-700 hover:bg-purple-800 focus:ring-4 focus:ring-purple-300 font-medium rounded-lg text-sm px-5 py-2.5 mb-2 dark:bg-purple-600 dark:hover:bg-purple-700 dark:focus:ring-purple-900 w-full">Calculate</button> 
                <h2 class="text-2xl">Result = {{ result }}</h2>
            </div>
        </form>
        </div>
    </section>
</template>
<style scoped>
.operator:checked + label {
    background-color: #1A56DB;
    color: #fff;
}
</style>