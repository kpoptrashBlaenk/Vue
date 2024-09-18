<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps<{
    keyDown: string;
    keySent: boolean;
}>()

const keyDown = ref(props.keyDown)
const keySent = ref(props.keySent)

function getKey(event: KeyboardEvent, lastPressed: string): void {
    if (lastPressed + event.key === "ea") {
        createAlert()
    }
    this.keyDown = event.key;
}

function createAlert(): void {
    alert("Alarm");
}

</script>

<template>
    <div class="mt-5">
        <h3>Event Modifiers</h3>
        <button @click.once="createAlert">
            This button can be used only once
        </button>
        <p>
            Do not type "ea"
            <input class="me-2 mt-3" @keydown="getKey($event, keyDown)" @keydown.enter="keySent = true" />{{ 'Key: ' +
                keyDown }} <span v-show="keySent"> | Sent</span>
        </p>
    </div>
</template>