<template>
    <h2 :value="appname"></h2>
    <ul>
        <Note v-for="note in dummyNotes" :key="note.id" :note="note"></Note>
    </ul>
</template>
<script>
import Note from "./components/notes/Note.vue";
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
                    description: "World card must be payed by 8th of July",
                    link: "https://www.garantibbva.com.tr/dijital-bankacilik/internet-bankaciligi"
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

ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>