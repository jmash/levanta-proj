<template>
    <div id="askMessage">
        <h1>{{ currDate }}</h1>
        <h2>{{ text }}</h2>
    </div>
</template>

<script>
    export default {
        name: "AskMessage",
        props: ["text", "currDate"]
    }
</script>
