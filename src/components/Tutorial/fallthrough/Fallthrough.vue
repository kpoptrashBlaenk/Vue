<script setup lang="ts">
import { ref } from 'vue'
import FallthroughExtended from './FallthroughExtended.vue';

const props = defineProps<{
    items: string[],
    newItem: string
}>()

const items = ref(props.items)
const newItem = ref(props.newItem)

function addItem() {
    items.value.push(newItem.value)
    newItem.value = ''
}

</script>

<template>
    <div class="mt-5">
        <h3>Fallthrough</h3>
        <ul>
            <FallthroughExtended v-for="x in items" :item-name="x" class="text-bg-success" />
        </ul>
        <input v-model="newItem">
        <button @click="addItem">Add</button>
    </div>
</template>