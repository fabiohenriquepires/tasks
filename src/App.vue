<template>
  <section class="todoapp">
    <header class="header">
      <h1>TASKS</h1>
    </header>
    
    
      <input-task></input-task>
      <task-list v-bind:todo-list="tasks"></task-list>
    
    
  </section>
</template>


<script>
import InputTask from './components/InputTask'
import TaskList from './components/TaskList'
import {Task} from './models/Task'

let tasks = [];
let task = new Task();
task.completed = false
task.title = 'Tarefa'
tasks.push(task)
tasks.push(task)
tasks.push(task)

export default {
  name: 'App',
  components: {
    InputTask,
    TaskList
  },
  data () {
    return {
      tasks: tasks
    }
  }
}
</script>

<style>
.header{
  font-size: 22px;
  background-color: #343a40;
  color: #fff;
  padding: 10px;
  height: 10%;
  text-align: center;
}

.todoapp {
 font-family: Helvetica;
 position: absolute;
 width: 100%;
 left: 0;
 top: 0;
}

.card {
  /* Add shadows to create the "card" effect */
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
}

/* On mouse-over, add a deeper shadow */
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}

/* Add some padding inside the card container */
.container {
  padding: 2px 16px;
}
</style>
