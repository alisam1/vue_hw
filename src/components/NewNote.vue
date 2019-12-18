<template>
       <div class="new-note">
           <label>Title</label>
            <input v-model ="note.title" type="text">
            <label>Description</label>
            <textarea v-model ="note.description"></textarea>
             <select id="note-select" v-model="note.select">
                 <option value="1">Все</option>
                 <option value="2">Важно</option>
                 <option value="3">Очень важно!</option>
            </select>
            <pre v-if="note.select">Сейчас выбрано: {{ note.select }}</pre>
            <button class = "btn btnPrimary" @click = "addNote">New note</button>
        </div>

</template>

<script>
export default {
    props:{
        note:{
            type: Object,
            required: true,
        }
    },
    methods:{
        addNote(){
            this.$emit('addNote', this.note)
        }
    }
    
}
</script>

<style lang="scss">
.new-note
{
    text-align: center;
}

</style>