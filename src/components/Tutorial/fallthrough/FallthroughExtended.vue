<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps<{
    itemName: string
}>()

const itemName = ref(props.itemName)

</script>

<template>
    <div>don't inherit</div>
    <li v-bind="$attrs">{{ itemName }}</li>
    <div>parents classes</div>
</template>