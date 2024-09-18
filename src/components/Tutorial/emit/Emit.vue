<script setup lang="ts">
import { ref } from 'vue'
import EmitExtended from './EmitExtended.vue';

export interface food {
    name: string
}

const props = defineProps<{
    foods: food[]
}>()

const foods = ref(props.foods)

function removeFoods(foodName: string): void {
    const index = foods.value.findIndex(food => food.name === foodName);
    foods.value.splice(index, 1);
}

</script>

<template>
    <div class="mt-5">
        <h3>Emit</h3>
        <div>
            <EmitExtended v-for="x in foods" :foodName="x.name" @remove="removeFoods" />
        </div>
    </div>
</template>