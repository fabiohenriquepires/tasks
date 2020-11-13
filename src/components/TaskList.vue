<template>
  <ul class="todo-list">
    <li v-for="(todo, index) in sortedTasks" class="task" :key="index">
      <input class="toggle" @click="completeTask(todo)" type="checkbox" />
      <label v-if="todo.completed" class="todo-completed">{{todo.title}}</label>
      <label v-else>{{todo.title}}</label>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["todoList"],
  computed: {
    sortedTasks: function () {
      let sorted = this.todoList.slice();
      return sorted.sort(function (a, b) {
        if (a.title < b.title) return -1;
        if (a.title > b.title) return 1;
        return 0;
      });
    },
  },
  methods: {
	  completeTask(task) {
		task.completed = !task.completed;
	  }
  }
};
</script>

<style>
.task:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}

.todo-list {
	margin: 0;
	padding: 0;
	list-style: none;
}
.todo-list li {
	position: relative;
	font-size: 24px;
	border-bottom: 1px solid #ededed;
}
.todo-completed{
  text-decoration: line-through;
}
.todo-list li:last-child {
	border-bottom: none;
}
.todo-list li.editing {
	border-bottom: none;
	padding: 0;
}
.todo-list li.editing .edit {
	display: block;
	width: 506px;
	padding: 12px 16px;
	margin: 0 0 0 43px;
}
.todo-list li.editing .view {
	display: none;
}
.todo-list li .toggle {
	text-align: center;
	width: 40px;
	height: 40px;
	/* auto, since non-WebKit browsers doesn't support input styling */
	height: auto;
	position: absolute;
	top: 0;
	bottom: 0;
	margin: auto 0;
	border: none; /* Mobile Safari */
	-webkit-appearance: none;
	appearance: none;
	display: table-cell;
    vertical-align: middle
}
.todo-list li .toggle:after {
	opacity: 0.2;
	content: url('../assets/yes_check.svg');
	
}
.todo-list li .toggle:checked:after {
	opacity: unset;
	content: url('../assets/yes_check.svg');
}
.todo-list li label {
	word-break: break-all;
	padding: 15px 60px 15px 15px;
	margin-left: 45px;
	display: block;
	line-height: 1.2;
	transition: color 0.4s;
}
.todo-list li.completed label {
	color: #d9d9d9;
	text-decoration: line-through;
}
.todo-list li .destroy {
	display: none;
	position: absolute;
	top: 0;
	right: 10px;
	bottom: 0;
	width: 40px;
	height: 40px;
	margin: auto 0;
	font-size: 30px;
	color: #cc9a9a;
	margin-bottom: 11px;
	transition: color 0.2s ease-out;
}
.todo-list li .destroy:hover {
	color: #af5b5e;
}
.todo-list li .destroy:after {
	content: '×';
}
.todo-list li:hover .destroy {
	display: block;
}
.todo-list li .edit {
	display: none;
}
.todo-list li.editing:last-child {
	margin-bottom: -1px;
}
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  .toggle-all,
  .todo-list li .toggle {
    background: none;
  }
  .todo-list li .toggle {
    padding: 20px 0px 0px 10px;
  }
  .toggle-all {
    -webkit-transform: rotate(90deg);
    transform: rotate(90deg);
    -webkit-appearance: none;
    appearance: none;
  }
}
</style>