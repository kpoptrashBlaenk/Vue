<script setup lang="ts">

defineProps<{
    vIfStock: number;
    vIfText: string;
}>()

</script>

<template>
    <div class="mt-5">
        <h3>v-if</h3>
        <p v-if="vIfStock > 3">in stock</p>
        <p v-else-if="vIfStock > 0">not much in stock</p>
        <p v-else>none in stock</p>

        <p v-if="vIfText.includes('word')">includes word</p>
        <p v-else>doesn't include word</p>
    </div>
</template>