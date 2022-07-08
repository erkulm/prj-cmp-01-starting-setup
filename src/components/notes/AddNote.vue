<template>
    <base-dialog title="Invalid Input" v-if="formIsInvalid" @close="setFormValid">
        <template #default>
            <p>One or more of input fields are empty</p>
            <p>Please make sure you enter all fields except link</p>
        </template>
        <template #actions>
            <base-button @click="setFormValid">Okay</base-button>
        </template>
    </base-dialog>
    <base-card>
        <h2>Add New Note</h2>
        <form @submit.prevent="submitNewNote">
            <div class="form-control">
                <label for="name">Name:</label>
                <input type="text" name="name" id="name" ref="nameInput" />
            </div>
            <div class="form-control">
                <label for="details">Details:</label>
                <textarea rows="4" name="details" id="details" ref="detailsInput" />
            </div>
            <div class="form-control">
                <label for="link">Link:</label>
                <input type="urll" name="link" id="link" ref="linkInput" />
            </div>
            <div>
                <base-button type="submit">Add Note</base-button>
            </div>
        </form>
    </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue'
import BaseDialog from '../UI/BaseDialog.vue';
export default {
    data() {
        return {
            formIsInvalid: false,
        }
    },
    components: { BaseButton, BaseDialog },
    inject: ['addNewNote'],
    methods: {
        submitNewNote() {
            const name = this.$refs.nameInput.value.trim();
            const details = this.$refs.detailsInput.value.trim();
            const link = this.$refs.linkInput.value.trim();

            if (name === '' || details === '') {
                this.formIsInvalid = true;
                return;
            }

            this.addNewNote(name, details, link);
            this.$refs.nameInput.value = '';
            this.$refs.detailsInput.value = '';
            this.$refs.linkInput.value = '';
        },
        setFormValid(){
            this.formIsInvalid = false;
        }
    }
}
</script>
<style scoped>
label {
    font-weight: bold;
    display: block;
    margin-bottom: 0.5rem;
}

input,
textarea {
    display: block;
    width: 100%;
    font: inherit;
    padding: 0.15rem;
    border: 1px solid #ccc;
}

input:focus,
textarea:focus {
    outline: none;
    border-color: #3a0061;
    background-color: #f7ebff;
}

.form-control {
    margin: 1rem 0;
}
</style>