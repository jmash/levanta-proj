<template>
    <input
        :value="value"
        @input="$emit('input', $event.target.value)"
        @keyup.enter="$emit('submit', $event.target.value)"
        placeholder="What did you do today?"
    />
</template>

<script>
    export default {
        name: "UserInput",
        props: ["value"],
    }

</script>
