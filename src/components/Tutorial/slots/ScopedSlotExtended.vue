<script setup lang="ts">

const localData = 'This is local data'
const array = [1, 2, 3]
</script>

<template>
    <div>
        <div>Above Slot</div>
        <slot name="botSlot" :localData="localData"></slot>
        <div>Under Slot</div>
        <ul>
            <slot name="array" v-for="(x, index) in array" :item="x" :key="index"></slot>
        </ul>
    </div>
</template>