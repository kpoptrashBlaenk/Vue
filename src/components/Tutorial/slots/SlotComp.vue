<script setup lang="ts">
import Slot from './Slot.vue'
</script>

<template>
    <div class="mt-5">
        <h3>Slots</h3>
        <Slot>
            <template v-slot:topSlot>
                <div class="fw-bold">Hello World!</div>
            </template>
            <template v-slot:botSlot>
                <div class="fw-bold">Goodbye World!</div>
            </template>
        </Slot>
    </div>
</template>