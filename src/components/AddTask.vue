<template>
    <div>

        <hr style="border-top:1px solid steelblue;margin:30px 0px">

        <form @submit="show">

            <label>Task Title</label>
            <input type="text" autocomplete="off" v-model="text" name="text" placeholder="ENYER THE TITLE" />

            <label>Task Date</label>
            <input type="text" autocomplete="off" v-model="date" name="date" placeholder="ENYER THE DATE" />

            <input id="remind" name="reminder" type="checkbox" v-model="reminder"/>
            <label for="remind">remind me</label>

            <input class="btn btn-block" type="submit" value="Save Task" style="background-color: green;"/>           
            <hr style="border-top:1px solid steelblue;margin:30px 0px">

       </form>

    </div>
</template>

<script>
export default {

    name:"AddTask",
    data(){
        return{
            text:'',
            date:'',
            reminder:false
        }
    },
    methods:{
        show(e){
            e.preventDefault()
            const newtask= {
                id : Math.floor( Math.random() * 10000 ),
                text : this.text,
                date : this.date,
                reminder : this.reminder
            }
            this.$emit('addtask', newtask)
            this.text = '',
            this.date = '',
            this.reminder = false
        }
    },
    emits:['addtask']
}
</script>

<style scoped>
div{  color: #2c3e50;
}
label{
    display: block;
    font-size: 18px;
}
label:last-of-type{
    display: inline-block;
    margin-left: 5px;
    font-size: 18px;
}
input[type='text']{
    padding: 5px;
    border-radius: 5px;
    border: 1px solid steelblue;
    width: 100%;
    margin-bottom: 10px;
}
input[type='text']:focus-visible{
    border: 1px solid #00f!important;
    outline: none;
}
input[type='checkbox']{
    padding: 5px;
    border-radius: 5px;
    margin-bottom: 10px;
    cursor: pointer;
}
</style>