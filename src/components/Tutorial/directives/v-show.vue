<script setup lang="ts">

defineProps<{
    vShow: boolean;
}>()

</script>

<template>
    <div class="mt-5">
        <h3>v-show</h3>
        <p v-show="vShow">v-show</p>
        <p v-show="!vShow">v-show</p>
    </div>
</template>