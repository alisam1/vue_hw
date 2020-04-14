<template>
     <div class="notes">
            <div class="note"
                 v-for="note in notes" :key="note.id"
                 :class="[{full: !grid}, note.select.class]"
                 >
                    <div class="note-header">
                    <div class="note-top">
                        <div @dblclick="editTitleNote(note)">
                        <div v-show="!note.edit_mode_title">{{ note.title }}</div>
                        <div v-show="note.edit_mode_title">
                            <input v-model="note.title" @keyup.enter="saveNoteTitle(note)" type="text" />
                        </div>
                    </div>
                    <p class="note-remove" @click="removeNote(id)">X</p>
                    </div>
                     <div @dblclick="editDescriptionNote(note)">
                        <div v-show="!note.edit_mode_desc">{{note.description}}</div>
                        <div v-show="note.edit_mode_desc">
                            <input v-model="note.description" @keyup.enter="saveNoteDescription(note)" type="text" />
                        </div>
                        </div>
                    <span>{{note.date}}</span>
                </div>
            </div>
        </div>
</template>


<script>
export default {
    props:{
        notes:{
            type: Array,
            required: true,
        },
        grid:{
            type: Boolean,
            required: true
        },
        selected:{
            type: Array,
            required: false
        },
        select:{
            type: String,
            required: false
        },
    },
    methods:{
        removeNote(index){
           console.log(`Note id - ${index} removed`)
           this.$emit('remove', index)
        },
         editTitleNote: function (note) {
                this.$set(note, 'edit_mode_title', true);
            },
        saveNoteTitle: function (note) {
                note.edit_mode_title = false;
        },
        editDescriptionNote: function (note) {
                this.$set(note, 'edit_mode_desc', true);
            },
        saveNoteDescription: function (note) {
                note.edit_mode_desc = false;
        },
         currentStatus(){
                    let status = this.note.select.class;
                    console.log(status)
        }
    }
}
</script>

<style lang="scss">
.notes
{
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    padding: 40px 0;
}

.note
{
    width: 48%;
    padding: 18px 20px;
    margin-bottom: 20px;
    background-color: #fff;
    border-radius: 6px;
    &.full
    {
        width: 100%;
    }
    &.greenS
    {
        border: 1px solid #1acc61;
    }
}

.green 
{
     box-shadow: 0 4px 14px rgba(25, 227, 35, 0.5);
}

.yellow 
{
     box-shadow: 0 4px 14px rgba(227, 197, 25, 0.5);
}

.red
{
   box-shadow: 0 4px 14px rgba(227, 25, 25, 0.5);
}

.note-header .red .note
{
    color: red;
}



.new-note textarea
{
    margin-bottom: 30px;
}

.note-remove
{
    cursor: pointer;
}

.note-header
{

    display: flex;
    flex-direction: column;;
    justify-content: space-between;
    margin-top: 0px;
    padding-top: 20px;
    padding-bottom: 30px;

    h1
    {
        font-size: 32px;
        text-align: center;
        margin-bottom: 30px;
        margin-top: 40px;
    }

    p 
    {
        font-size: 22px;
        color: #999999;
        margin: 20px 0;
        margin-top: 0px;
    }
     span 
    {
        font-size: 14px;
        color: #999;
    }
    svg 
    {
        margin-right: 12px;
        color: #999999;
        &.active 
        {
            color: #402caf;
        }
        &:last-child 
        {
            margin-right: 0;
        }
    }
}


.search-block
{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.note-top
{
     display: flex;
    align-items: center;
    justify-content: space-between;
}

</style>