<script setup lang="ts">

const emit = defineEmits<{
    (e: 'remove', foodName: string): void
}>()

const props = defineProps<{
    foodName: string
}>()

function removeFood(): void {
    emit('remove', props.foodName)
}

</script>

<template>
    <p>
        {{ foodName }}
        <button class="ms-2" @click.stop="removeFood">Remove</button>
    </p>
</template>