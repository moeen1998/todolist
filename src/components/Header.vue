<template>
    <header>
        <h1>{{title}}</h1>
        <div v-if="status">
            <button style="background-color: red;" @click="$emit('toggle')" class="btn">hide the form</button>
        </div>
        <div v-else>
            <button style="background-color: green;" @click="$emit('toggle')" class="btn">show the form</button>
        </div>
    </header>
</template>

<script>

export default {
    name:'Header',
    // لو عايز بس ابعت داتا من الاب 
    // props:['title']

    // لو عايز ابعت داتا من الاب و احدد نوعها 
    // props:{
    //     title:String
    // }

    // لو عايز ابعت داتا من الاب واحدد نوعها و الديفولت بتاعها
    props:{
        title:{
            type: String,
            default:"hello from props"
        },
        status: Boolean
    },
    emits:['toggle']
}
</script>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
      color: #2c3e50;

}

</style>
