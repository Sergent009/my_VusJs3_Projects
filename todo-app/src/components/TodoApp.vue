<template>
<h1>ToDo List - Abdul Mannan Khan</h1>

<div v-if="!editing">
<input class="inputfield" type="text" v-model="task">
<button class="addButton" @click="storeTask">Add Task</button>
</div>

<div v-else>
<input type="text" v-model="task">
<button @click="updateTask">Update Task</button>
</div>

<!-- <ol>     -->
  <li class="displayTasks" v-for="(task, index) in tasks" :key="task">
      {{ task }}
      <button @click="editTask(index, task)">Edit Task</button> 
      <button @click="deleteTask(index)">Delete Task</button>
  </li>
<!-- </ol> -->

</template>

<script>
export default {
  name: 'TodoApp',

  data(){
    return{
      editing: false,
      selectedIndex: null,
      task: '',
      tasks: ['go to market', 'buy a pen'],
    }
  },
  methods: {
    storeTask(){
      this.tasks.push(this.task)
      this.task = ''
    },

    editTask(index, task){
      this.task = task
      this.selectedIndex = index
      this.editing = true
    },

    updateTask(){
      this.tasks.splice(this.selectedIndex, 1, this.task)
      this.editing = false
    },

    deleteTask(index){
      this.tasks.splice(index, )
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Satisfy&display=swap');
h1{
  color: white;
  margin-left: 400px;
  width: 500px;
  height: 40px;
  background: linear-gradient(100deg, rgb(182, 121, 182), rgb(85, 152, 179));
  border: 3px solid black;
  border-radius: 10px;
  font-family: 'Satisfy', cursive;
}


.displayTasks{
  padding-top: 10px;
  margin-top: 28px;
}

.inputfield{
  margin-top: 60px;
  margin-left: 20px;
  width: 400px;
  height: 30px;
  font-size: 18px;
  border: 1px solid black;
  border-radius: 4px;
  font-family:  'Satisfy', cursive;
  color: rgb(245, 140, 4);
}

.addButton{
  margin-left: 0px;
  width: 100px;
  height: 34px;
  font-size: 19px;
  font-family:  'Satisfy', cursive;
  border: 1px solid black;
  border-radius: 4px;
  background: rgb(124, 97, 124);
  color: rgb(231, 145, 33);
  cursor: pointer;
}
.addButton:hover{
  background:  rgb(231, 145, 33);
  color: rgb(124, 97, 124);
}
</style>
