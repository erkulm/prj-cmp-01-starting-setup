<template>
    <section>
        <div>
            <label :for="note.id">Name</label>
            <input type="text" disabled :id="note.id" :value="note.name" />
        </div>
        <div>
            <label :for="note.id">Detail</label>
            <input type="text" disabled :id="note.id" :value="note.description" />
        </div>
    </section>
</template>

<script>
export default {
    props: {
        note: {
            type: Object,
            required: true
        }
    },
}
</script>