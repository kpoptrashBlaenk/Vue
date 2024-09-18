<script setup lang="ts">
import { ref } from 'vue';

const props = defineProps<{
    click: boolean;
    isInput: boolean;
    typingTimer: number | null;
    ontype: string;
    xPos: number;
}>()

const click = ref(props.click)
const isInput = ref(props.isInput)
const typingTimer = ref(props.typingTimer)
const ontype = ref(props.ontype)
const xPos = ref(props.xPos)

function setIsInput(): void {
      isInput.value = true;

      // because no on stop typing
      clearTimeout(typingTimer.value);

      typingTimer.value = setTimeout(() => {
        isInput.value = false;
      }, 500);
    }

function mousePos(event: MouseEvent): void {
    xPos.value = event.offsetX;
}

</script>

<template>
    <div class="mt-5">
        <h3>@click @input @mouseover @mousemove</h3>
        <button @click="ontype === 'click' ? ontype = 'mouseover' : ontype = 'click'">
            {{ ontype }}
        </button>
        <button @[ontype]="click ? click = false : click = true">
            {{ click }}
        </button>
        <p>
            <input class="me-2 mt-2" :disabled="!click" @input="setIsInput" />{{
                isInput ? 'writing...' : 'not writing' }}
        </p>
        <p @mousemove="mousePos">{{ 'x Position: ' + xPos }}</p>
    </div>
</template>