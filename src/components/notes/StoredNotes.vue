<template>
    <ul>
        <Note v-for="note in notes" :key="note.id" :note="note"></Note>
    </ul>
</template>
<script>
import Note from './Note.vue'
export default {
    components:{
        Note
    },
    inject: ['notes']
}
</script>

<style scoped>

ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>