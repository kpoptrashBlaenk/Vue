<script setup lang="ts">
import { ref, computed } from 'vue'
import CompOne from './CompOne.vue'
import CompTwo from './CompTwo.vue'

const props = defineProps<{
    toggleValue: boolean
}>()

const toggleValue = ref(props.toggleValue)

const compMap = {
    'comp-one': CompOne,
    'comp-two': CompTwo
}

const activeComp = computed((): 'comp-one' | 'comp-two' => {
    if (toggleValue.value) {
        return 'comp-one'
    } else {
        return 'comp-two'
    }
})

</script>

<template>
    <div class="mt-5">
        <h3>Dynamic components</h3>
        <button @click="toggleValue = !toggleValue">
            Switch component
        </button>
        <component :is="compMap[activeComp]"></component>
    </div>
</template>