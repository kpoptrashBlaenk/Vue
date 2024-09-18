<script setup lang="ts">

interface VBinds {
    class: string;
    style: string;
}

defineProps<{
    vBinds: VBinds;
    background: boolean;
    classObject: Record<string, boolean>;
}>();

</script>

<template>
    <div class="mt-5">
        <h3>Classes:</h3>
        <p :class="[vBinds.class, background ? 'bg-primary-subtle' : '']" :style="vBinds.style">
            Conditional Background Color
        </p>
        <p :class="classObject">Class Object</p>
    </div>
</template>
