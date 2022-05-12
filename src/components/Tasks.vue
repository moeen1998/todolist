<template>
    <div v-for="(task,index) in tasks" :key="index">

       <Task @toggle="$emit('toggle',task.id)" @deleteitem="$emit('deletetask',task.id)" :task="task"/>
       
    </div>
</template>

<script>
import Task from './Task.vue'

export default {
    name:"Tasks",
    props:{
        tasks:Array,
    },
    components:{
        Task
    },
// ممكن اعمل ال ايمت كدا بالشكل دااااااا
    // deletetask(id){
    //         this.$emit("deletetask",id)
    //     }
    emits:['deletetask','toggle']
    
}
</script>

<style>

</style>