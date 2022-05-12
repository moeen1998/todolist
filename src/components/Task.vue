<template>
  <div @dblclick="$emit('toggle')" :class="[task.reminder ? 'reminder task' : 'task']">

      <div class="left">
          <h3>{{task.text}}</h3>
          <p>{{task.date}}</p>
      </div>

      <div class="right" >
          <div @click="$emit('deleteitem')">
              <i style="color: red; cursor: pointer;font-size: 20px;" class="fa-solid fa-xmark"></i>
          </div>  
      </div>

  </div>
</template>

<script>

export default {
    name:"Task",
    props:{
        task:Object
    },
    // ممكن اعمل ال ايمت بالشكل دا 
    // methods:{
    //     deleteitem(){
    //         this.$emit("deleteitem")
    //     }
    // },
    emits:['deleteitem','toggle']
}
</script>

<style scoped>
.task{
    display: flex;
    justify-content: space-between;
    background-color: #f4f4f4;
    margin-bottom: 5px;
    padding: 5px;
    color: #2c3e50;

}
.reminder{
    border-left: 2px solid green;
}
</style>