<template>
     <div class="notes">
            <div class="note" :class = "{full: !grid}" v-for="(note, index) in notes" :key="index">
                <div class="note-header">
                    <div class="note-top">
                    <p>{{note.title}}</p>
                    <p class="note-remove" @click="removeNote(index)">X</p>
                    </div>
                    <p>{{note.description}}</p>
                    <span>{{note.date}}</span>
                    <span :class="{green: value == 1, yellow: value == 2, green: value == 3}">{{note.select}}</span>
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
        select:{
            type: Array,
            required: true
        },
    },
    methods:{
        removeNote(index){
           console.log(`Note id - ${index} removed`)
           this.$emit('remove', index)
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
    &.all
    {
        border: green;
    }
    &.completed
    {
        border: green;
    }
    &.all
    {
        border: green;
    }
}

.red
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

.note-top
{
     display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>