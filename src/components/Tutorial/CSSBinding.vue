<script setup lang="ts">

defineProps<{
    classList0: string;
    classList1: string;
}>()

</script>

<template>
    <div class="mt-5">
        <h3>CSS Binding</h3>
        <div class="text-danger" :class="[classList0, classList1]">
            This has class="" and :class=""
        </div>
    </div>
</template>