<script setup lang="ts">

defineProps<{ msg: string }>()

</script>

<template>
  <div id="intro" class="custom">
    <h3>Intro</h3>
    <p>{{ msg }}</p>
  </div>
</template>
