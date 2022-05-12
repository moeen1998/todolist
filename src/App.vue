<template>
  <div class="container">

    <Header @toggle="toggleform" :status="showaddtask" title="task tracker"/>

    <div v-show="showaddtask">
      <AddTask @addtask="Add_Task"/>
    </div>

    <Tasks @toggle="toggle" @deletetask="deletetask" :tasks="tasks"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data(){
    return {
      tasks:[],
      showaddtask : false
    }
  },
  created(){
    this.tasks = [
      {
        id: 1,
        text: "first task",
        date: "march 1st at 2:30pm",
        reminder: true
      },
      {
        id: 2,
        text: "second task",
        date: "may 1st at 2:30pm",
        reminder: false
      },
      {
        id: 3,
        text: "therd task",
        date: "april 1st at 2:30pm",
        reminder: true
      },
    ]
  },
  methods:{
    toggleform(){
      this.showaddtask = !this.showaddtask
    },
    Add_Task(newtask){
      this.tasks =  [ ...this.tasks , newtask ]
    },
    deletetask(id){

      if(confirm("Are You Sure !!!")){
        this.tasks = this.tasks.filter((task) => task.id != id)
      }  
    },
    toggle(id){
      this.tasks = this.tasks.map(
        (task) => task.id === id ? 
        {...task,reminder: !task.reminder} : 
        task)
    }
  }

}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  text-transform: capitalize;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
