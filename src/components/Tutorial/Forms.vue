<script setup lang="ts">
import { ref } from 'vue'

interface item {
    name: string,
    number: number,
    important: boolean,
    found: boolean,
}

const props = defineProps<{
    itemName: string | null,
    itemNumber: number | null,
    itemImportant: boolean,
    list: item[]
}>()

const itemName = ref(props.itemName)
const itemNumber = ref(props.itemNumber)
const itemImportant = ref(props.itemImportant)
const list = ref(props.list)

function addItem() {
    if (itemName.value && itemNumber.value) {
        const item = {
            name: itemName.value,
            number: itemNumber.value,
            important: itemImportant.value,
            found: false,
        };

        list.value.push(item);
        itemName.value = null;
        itemNumber.value = null;
        itemImportant.value = false;
    }
}

</script>

<template>
    <div class="mt-5">
        <h3>Forms</h3>
        <form @submit.prevent="addItem">
            <p>Item name: <input v-model="itemName" /></p>
            <p>How many: <input v-model="itemNumber" /></p>
            <button class="me-2" type="submit">Add item</button>
            <label>
                <input type="checkbox" v-model="itemImportant" />
                {{ itemImportant ? 'important' : 'not important' }}
            </label>
        </form>
        <ul>
            <li v-for="item in list" :class="item.found ? 'text-success' : item.important ? 'text-danger' : 'text-dark'"
                style="cursor: pointer" @click="item.found = !item.found">
                {{ item.name }}, {{ item.number }}
            </li>
        </ul>
    </div>
</template>