<template>
  <div id="task-list">
    <input v-on:keyup.enter="addTask()" v-model="newTask" placeholder="New Task" class="input my-input" />
    <input type="text" hidden >
    <ul class="list-group">
      <li v-for="(task,index) in tasks" :key="index" class="list-group-item my-item">{{task.task}}
        <button v-on:click="delTask(index)" class="my-del-btn">Delete</button>
        <input type="checkbox" v-model="task.complete"/>
        <button v-if="task.complete" class='my-btn-complete'>Complete</button>
        
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TaskList",
  data(){ return {
      tasks: [{task: 'My Task', complete:false}],
    newTask: ''
  }
},
  methods: {
    addTask: function() {
      this.tasks.push({ task: this.newTask, complete: false})
      this.newTask = ''
    },
    delTask: function(index){
      this.tasks.splice(index, 1)
    },
    markComplete: function(index){
      this.task = this.tasks.indexOf(index)
      if(this.task.complete){
        this.task.complete= false
      } else {
        this.task.complete = true
      }
    }
  }
};
</script>

<style lang="scss" scoped>
h1 {
  font-weight: 800;
  color: rgb(4, 4, 39);
  font-size: 2em;
  text-align: left;
  padding: 1%;
}

p {
  text-align: left;
  padding: 1%;
}

.my-btn {
  /*border: solid lightgreen 0.1em;
  background: white;
  border-radius: 5px;
  align-self: right;
  margin-right: 0.8%;*/
  display: hidden;
}

.my-btn-complete {
  border: solid rgb(80, 201, 80) 0.1px;
  background:  rgb(80, 201, 80);
  color: aliceblue;
  border-radius: 5px;
  align-self: right;
  margin-right: 0.8%;
}

.my-del-btn{
  border: solid red 0.1em;
  background: white;
  border-radius: 5px;
  align-self: right;
}

input{
  padding: 0;
  margin:0;
  vertical-align: middle;
}

.my-input{
  padding: 1%;
  margin-bottom: 1%;
}

li {
  text-align: left;
}

.my-item{
  padding: 0.8%;
  button{
    float: right;
  }
}
</style>