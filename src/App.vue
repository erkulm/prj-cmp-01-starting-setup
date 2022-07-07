<template>
    <h2 :value="appname"></h2>
    <ul>
        <li v-for="note in dummyNotes" :key="note.id">
            <Note :note="note"></Note>
        </li>
    </ul>
</template>
<script>
import Note from "./components/Note.vue";
export default {
    data() {
        return {
            appname: "notes",
            dummyNotes: [
                {
                    id: 1,
                    name: "Credit Card Payment",
                    description: "Bonus card must be payed by 7th of July"
                },
                {
                    id: 2,
                    name: "Credit Card Payment",
                    description: "World card must be payed by 7th of July"
                },
                {
                    id: 3,
                    name: "Credit Payment",
                    description: "Credit payment is due on 5fth of august"
                }
            ]
        };
    },
    components: { Note }
}
</script>