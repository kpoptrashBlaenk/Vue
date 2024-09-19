<template>
    <Teleport to="#intro">
        <div id="teleport" class="mt-5">
            <h3>
                Teleport
            </h3>
            <div>I have been teleported here. I was supposed to come after Dynamic Components.</div>
        </div>
    </Teleport>
</template>

# Keeps the styling too
<style scoped>
#teleport {
    background-color: aquamarine;
    color: blue;
}
</style>