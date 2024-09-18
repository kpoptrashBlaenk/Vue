<script setup lang="ts">

defineProps<{ msg: string }>()

</script>

<template>
  <div class="custom">
    <h3>Intro</h3>
    <p>{{ msg }}</p>
  </div>
</template>
