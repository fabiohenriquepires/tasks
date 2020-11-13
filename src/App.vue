<template>
  <section class="todoapp">
    <header>
      <h1>TASKS</h1>
    </header>
    <body>
      <div class="card">
        <input-task @newTask="addTask"></input-task>
        <task-list v-bind:todo-list="tasks"></task-list>
      </div>
    </body>
  </section>
</template>


<script>
import InputTask from "./components/InputTask";
import TaskList from "./components/TaskList";
import { Task } from "./models/Task";

export default {
  name: "App",
  components: {
    InputTask,
    TaskList,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    addTask(task) {
      this.tasks.push(task);
    },
  },
};
</script>

<style>
header {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  font-size: 20px;
  background-color: #e53935;
  color: #fff;
  padding: 4px;
  text-align: center;
}

body {
  display: flex;
  justify-content: center;
  padding-top: 10px;
}

.todoapp {
  font-family: Helvetica;
  position: absolute;
  width: 100%;
  left: 0;
  top: 0;
}

.card {
  display: inline-block;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  max-width: 90%;
  min-width: 30%;
  max-height: 500px;
  overflow: auto;
}

/* On mouse-over, add a deeper shadow */
/* .card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
} */
</style>
