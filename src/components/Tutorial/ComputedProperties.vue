<script setup lang="ts">
import { ref, computed } from 'vue'

const props = defineProps<{
    checkboxVal: boolean
}>()

const checkboxVal = ref(props.checkboxVal)

const isImportant = computed(() => {
    if (checkboxVal.value) {
        return "yes";
    } else {
        return "no";
    }
})

</script>

<template>
    <div class="mt-5">
        <h3>Computed Properties</h3>
        <p>
            <input class="me-2" type="checkbox" v-model="checkboxVal" />
            {{ isImportant }}
        </p>
    </div>
</template>
