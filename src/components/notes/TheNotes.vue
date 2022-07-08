<template>
    <base-card id="seletedTab">
        <base-button :mode="storedNotesButtonMode" @click="setSelectedTab('add-note')">New Note</base-button>
        <base-button :mode="addNoteButtonMode" @click="setSelectedTab('stored-notes')">Notes</base-button>
    </base-card>
    <component :is="selectedTab"></component>
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
            selectedTab: 'stored-notes'
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
        }
    }, provide() {
        return {
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
            ]
        }
    }
}
</script>

<style scoped>
    #seletedTab{
       display: flex;
  justify-content: center;
    }
</style>