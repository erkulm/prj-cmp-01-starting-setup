<template>
    <base-card id="seletedTab">
        <base-button :mode="storedNotesButtonMode" @click="setSelectedTab('add-note')">New Note</base-button>
        <base-button :mode="addNoteButtonMode" @click="setSelectedTab('stored-notes')">Notes</base-button>
    </base-card>
    <keep-alive>
        <component :is="selectedTab"></component>
    </keep-alive>
</template>

<script>
import StoredNotes from './StoredNotes.vue';
import AddNote from './AddNote.vue';

export default {
    components: {
        StoredNotes,
        AddNote
    },
    data() {
        return {
            selectedTab: 'stored-notes',
            notes: [
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
            ],
        };
    },
    computed: {
        storedNotesButtonMode() {
            return this.selectedTab === 'stored-notes' ? null : 'flat';
        },
        addNoteButtonMode() {
            return this.selectedTab === 'add-note' ? null : 'flat';
        }
    },
    methods: {
        setSelectedTab(tab) {
            debugger;
            this.selectedTab = tab;
        },
        addNewNote(name, description, link) {
            const newNote = {
                id: new Date().toISOString(),
                name: name,
                description: description,
                link: link,
            };
            this.notes.unshift(newNote);
            this.selectedTab = 'stored-notes';
        },
        removeNote(id) {
            this.notes.splice(this.notes.findIndex(n => n.id === id), 1);
        }
    }, provide() {
        return {
            addNewNote: this.addNewNote,
            notes: this.notes,
            removeNote: this.removeNote,
        }
    }
}
</script>

<style scoped>
#seletedTab {
    display: flex;
    justify-content: center;
}
</style>