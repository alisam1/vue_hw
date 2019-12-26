<template>
       <div class="new-note">
           <label>Title</label>
            <input v-model ="note.title" type="text">
            <label>Description</label>
            <textarea v-model ="note.description"></textarea>
            <select 
                    @change="select"
                    v-model="note.select">
            <option v-for="option in options" :key="option.value" :class="[option.green ?'green':'', option.yellow ?'yellow':'', option.red ?'red':'', ]">
                {{ option.text }}
            </option>
            </select>
            <span 
            :class="{
            'greenS': note.select === 'Стандартная',
            'yellowS': note.select === 'Важная',
            'redS': note.select === 'Очень важная',
            }" 
            class="select">{{ note.select }}</span>
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
            options: [
            { 
                text: 'Стандартная', 
                value: 'А', 
                green: true,
                yellow: false,
                red: false,
            },
            { 
                text: 'Важная', 
                value: 'Б',
                green: false,
                yellow: true,
                red: false,
            },
            { 
                text: 'Очень важная', 
                value: 'В', 
                green: false,
                yellow: false,
                red: true,
            }
            ]
                }
    },
    methods: {
        addNote(){
            this.$emit('addNote', this.note)
        },
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