<script setup lang="ts">
import { computed, ref } from 'vue';
import PersonList from './PersonList.vue';

const inputtingName = ref<string>('')
const inputtingAge = ref<number>(0)

const emit = defineEmits(['register'])

const register = (name: string, age: number) => {
    const person = {id: Math.random(), name: inputtingName.value, age: inputtingAge.value}
    emit('register', person)

    inputtingName.value = ''
    inputtingAge.value = 0
}

const nameLengthLimit = 15

const isValidName = computed(()=> {
    if (inputtingName.value.length >= nameLengthLimit) {
        return false
    } else {
        return true
    }
})

const color = computed(()=> {
    return isValidName.value ? 'white' : 'rgb(244, 194, 190)'
})
</script>

<template>
    <div class="form-container">
        <div class="input-container">
            <div class="input-column">
                <span>name:</span>
                <input class="input-name" v-model="inputtingName" />
            </div>
            <span class="error-message" v-if="!isValidName">{{ nameLengthLimit }} characters or less, please</span>
            <div class="input-column">
                <span>age:</span>
                <input class="input" type="number" v-model="inputtingAge" />
            </div>
        </div>
        <button :disabled="!isValidName" class="regsiter-button" @click="register(inputtingName!, inputtingAge!)">register</button>
    </div>
</template>

<style scoped>
.form-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: rgba(255, 241, 226);
    padding: 24px 0;
    width: 50%;
    margin-bottom: 12px;
    border-radius: 4px;
}

.input-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 50px;
    margin-bottom: 20px;
}

.input-column {
    width: 200px;
    display: flex;
    justify-content: space-between;
}

.input-name {
    background-color:  v-bind(color);
}

input {
    width: 120px;
    margin-bottom: 8px;
}

span {
    font-size: 20px;
    font-weight: bold;
}

.error-message {
    font-size: 12px;
    color: rgb(244, 194, 190);
}
</style>
