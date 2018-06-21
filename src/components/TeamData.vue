<template>
    <div id="teamData">
        <div v-for="mook in mooks">
            <ul>
                <li>{{ mook.name }}</li>
                <li>{{ mook.message }}</li>
                <li>{{ new Date(mook.submitTime.seconds).toLocaleTimeString() }}</li>
            </ul>
            <span @click="$emit('removePost', $event.target.id)" :id="mook['.key']">X</span>
        </div>
    </div>
</template>

<script>
// mooks object temporary until database is hooked up
export default {
    name: "TeamData",
    props: ["mooks"]
}
</script>
