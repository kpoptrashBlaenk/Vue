<script setup lang="ts">
import Slot from './ScopedSlotExtended.vue'
</script>

<template>
    <div class="mt-5">
        <h3>Slots</h3>
        <Slot>
            <template v-slot:botSlot="slotProps">
                <div class="fw-bold">
                    Goodbye World! Received Data from child: {{ slotProps.localData }}
                </div>
            </template>
            <template v-slot:array="slotProps">
                <li>{{ slotProps.item }}</li>
            </template>
        </Slot>
    </div>
</template>