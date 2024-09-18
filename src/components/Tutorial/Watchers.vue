<script setup lang="ts">
import { ref, watch } from 'vue';

const props = defineProps<{
    rangeVal: number,
    watchX: number,
    watchXDiff: number,
    watcherInput: string,
    watcherFeedback: string,
    watcherEmailValid: string
}>()

const rangeVal = ref(props.rangeVal)

const watchX = ref(props.watchX)
const watchXDiff = ref(props.watchXDiff)

const watcherInput = ref(props.watcherInput)
const watcherFeedback = ref(props.watcherFeedback)
const watcherEmailValid = ref(props.watcherEmailValid)

function updateXPos(event: MouseEvent): void {
    watchX.value = event.offsetX;
}

watch(() => rangeVal.value, (val: number): void => {
    if (val > 20 && val < 60) {
        if (val < 40) {
            rangeVal.value = 20;
        } else {
            rangeVal.value = 60;
        }
    }
})

watch(() => watchX.value, (newVal: number, oldVal: number): void => {
    watchXDiff.value = newVal - oldVal
})

watch(() => watcherInput.value, (newVal: string, oldVal: string): void => {
    if (newVal === "") {
        watcherFeedback.value = "Enter an email address.";
        watcherEmailValid.value = "";
        return;
    }

    switch (`${newVal.includes("@")}${oldVal.includes("@")}`) {
        case "truetrue":
            watcherFeedback.value = "Email still valid.";
            watcherEmailValid.value = "is-valid";
            break;
        case "truefalse":
            watcherFeedback.value = "Email is now valid.";
            watcherEmailValid.value = "is-valid";
            break;
        case "falsetrue":
            watcherFeedback.value = "Email is not valid anymore.";
            watcherEmailValid.value = "is-invalid";
            break;
        case "falsefalse":
            watcherFeedback.value = "Email is not valid.";
            watcherEmailValid.value = "is-invalid";
            break;
    }
})

</script>

<template>
    <div class="mt-5">
        <h3>Watchers</h3>
        <p>
            <input class="me-2" type="range" v-model="rangeVal" />{{ rangeVal }}
        </p>
        <div @mouseover="updateXPos">{{ watchXDiff }}</div>
        <p>
            <input class="form-control mt-3" :class="watcherEmailValid" v-model="watcherInput" />
            {{ watcherFeedback }}
        </p>
    </div>
</template>