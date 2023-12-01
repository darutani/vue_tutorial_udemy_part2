<script setup lang="ts">
import { ref } from 'vue';

// type Persons = {
//     name: string,
//     age: number,
// }

const Persons = ref([{id: 0, name: 'John', age: 17}])

const deleteButton = (id: number) => {
    Persons.value = Persons.value.filter(p => p.id != id)
}
</script>

<template>
    <div>
        <div v-for="person in Persons" :key="person.id">
            <span>{{ person.name }}</span>
            <span>{{ person.age }}</span>
            <button @click="deleteButton(person.id)">delete</button>
        </div>
    </div>
</template>

<style>
</style>
