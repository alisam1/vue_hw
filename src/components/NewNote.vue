<template>
       <div class="new-note">
           <label>Title</label>
            <input v-model ="note.title" type="text">
            <label>Description</label>
            <textarea v-model ="note.description"></textarea>
            <select v-model="selected">
            <option v-for="option in options" :key="option.value">
                {{ option.text }}
            </option>
            </select>
            <span>Выбрано: {{ selected }}</span>
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
     data() {
            return {
            selected: 'А',
            options: [
            { text: 'Один', value: 'А' },
            { text: 'Два', value: 'Б' },
            { text: 'Три', value: 'В' }
            ]
                }
    },
    methods: {
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

.green option
{
    color: green;
}


</style>