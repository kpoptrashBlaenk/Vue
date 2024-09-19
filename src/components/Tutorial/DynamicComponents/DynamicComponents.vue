<script setup lang="ts">
import { ref, computed } from 'vue'
import CompOne from './CompOne.vue'
import CompTwo from './CompTwo.vue'
import CompThree from './CompThree.vue'

const props = defineProps<{
    toggleValue: boolean,
    compName: 'comp-one' | 'comp-two' | 'comp-three'
}>()

const toggleValue = ref(props.toggleValue)
const compName = ref(props.compName)

const compMap = {
    'comp-one': CompOne,
    'comp-two': CompTwo,
    'comp-three': CompThree
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
        <!-- KeepAlive saves changes in component (changed by include/exclude), requires children to have a defined name -->
        <KeepAlive include="comp-one">
            <component :is="compMap[activeComp]"></component>
        </KeepAlive>
        <KeepAlive exclude="comp-one">
            <component :is="compMap[activeComp]"></component>
        </KeepAlive>
        <!-- max 1 means that only the last 1 component will be remembered -->
        <label><input type="radio" name="rbgComp" v-model="compName" :value="'comp-one'"> One</label>
        <label><input type="radio" name="rbgComp" v-model="compName" :value="'comp-two'"> Two</label>
        <label><input type="radio" name="rbgComp" v-model="compName" :value="'comp-three'"> Three</label>
        <KeepAlive :max="2">
            <component :is="compMap[compName]"></component>
        </KeepAlive>
    </div>
</template>