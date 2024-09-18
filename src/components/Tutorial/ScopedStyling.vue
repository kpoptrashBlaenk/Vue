<template>
    <div class="mt-5">
        <h3>Scoped Styling</h3>
        <div class="custom">
            Global Styling: Intro also has this class
        </div>
    </div>
</template>

<style>
.custom {
    background-color: blueviolet;
}
</style>

<style scoped>
.custom {
    font-family: 'Times New Roman', Times, serif;
}
</style>