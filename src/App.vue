<template>
    <h2 :value="appname"></h2>
    <the-header :title="appname"></the-header>
    <the-notes></the-notes>
</template>
<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheNotes from './components/notes/TheNotes.vue'

export default {
    data() {
        return {
            appname: "notes",
        };
    },
    components: {  TheHeader, TheNotes}
}
</script>

<style >
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
    box-sizing: border-box;
}

html {
    font-family: 'Roboto', sans-serif;
}

body {
    margin: 0;
}

</style>