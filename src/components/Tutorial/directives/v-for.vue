<script setup lang="ts">

interface VForItem {
    class: string;
    text: string;
}

defineProps<{
    vForArray: VForItem[]
}>()

</script>

<template>
    <div class="mt-5">
        <h3>v-for</h3>
        <ol>
            <li v-for="(x, index) in vForArray" :class="x.class">
                {{ x.text + ' Index: ' + index }}
            </li>
        </ol>
    </div>
</template>