<template>
    <div id="teamData">
        <ul v-for="mook in mooks">
            <li>{{ mook.name }}</li>
            <li>{{ mook.message }}</li>
            <li>{{ mook.submitTime }}</li>
        </ul>
    </div>
</template>

<script>
// mooks object temporary until database is hooked up
export default {
    name: "TeamData",
    props: ["mooks"]
}
</script>
