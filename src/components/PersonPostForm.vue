<script setup lang="ts">
import { ref } from 'vue';
import PersonList from './PersonList.vue';

const inputtingName = ref<string>()
const inputtingAge = ref<number>()

const buttonRegister = (name: string, age: number) => {
    console.log('registerのボタン')
    const person = {id: Math.random, name, age}

    inputtingName.value = ''
    inputtingAge.value = undefined

}
</script>

<template>
    <div>
        <div>
            <span>name:</span>
            <input v-model="inputtingName">
        </div>
        <div>
            <span>age:</span>
            <input type="number" v-model="inputtingAge">
        </div>
        <button @click="buttonRegister(inputtingName!, inputtingAge!)">register</button>
    </div>
</template>

<style>
</style>
