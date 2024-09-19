<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios'

const filetypes = [
    'txt',
    'json',
    'api'
]

let filetypesIndex = 0

const data = ref('empty')

async function fetchData(): Promise<void> {

    if (filetypesIndex >= filetypes.length - 1) {
        filetypesIndex = 0
    } else {
        filetypesIndex++
    }

    let response

    switch (filetypes[filetypesIndex]) {
        case 'txt':
            response = await fetch(`./Vue/src/components/Tutorial/http requests/file.txt`)
            data.value = await response.text()
            break;
        case 'json':
            response = await fetch(`./Vue/src/components/Tutorial/http requests/file.json`)
            data.value = await response.json()
            break;
        case 'api':
            response = await axios.get("https://random-data-api.com/api/v2/users")
            data.value = response.data
            break;
    }
}

</script>

<template>
    <div class="mt-5">
        <h3>HTTP Request</h3>
        <button @click="fetchData()">Fetch Data</button>
        <div v-if="filetypes[filetypesIndex] === 'json'" v-for="object in data">{{ object.text }}</div>
        <div v-else-if="filetypes[filetypesIndex] === 'api'"> {{ `${data.first_name} ${data.last_name}` }}</div>
        <div v-else>{{ data }}</div>
    </div>
</template>