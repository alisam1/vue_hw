<template>
       <div class="new-note">
           <label>Title</label>
            <input v-model ="note.title" type="text">
            <label>Description</label>
            <textarea v-model ="note.description"></textarea>
            
            <select @change="selected" v-model="note.select">
               <option v-for="(item, index) in note.priority" :value="item" :key="index">{{ item.name }}</option>
            </select>
            <button class = "btn btnPrimary" @click = "addNote">New note</button>
        </div>

</template>

<script>
export default {
    props:{
        note:{
            type: Object,
            required: true,
        },
        selected:{
            type: Array,
            required: false
        },
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
    display: flex;
    flex-direction: column;
}

.new-note select
{
    width: 200px;
    margin: 0 auto;
    margin-bottom: 20px;
}

.new-note span
{
    width: 200px;
    margin: 0 auto;
    margin-top: 10px;
    margin-bottom: 40px;
}

.new-note button
{
    width: 250px;
    margin: 0 auto;
}
    .greenS
    {
        color: aquamarine;
    }

    .yellowS
    {
        color: yellow;
    }

    .redS
    {
        color: #8B0000;
    }



</style>