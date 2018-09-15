<template>
    <div>
        <TodoInput 
			v-model="newTodo"
			placeholder="New todo"
			@keydown.enter="addTodo"
		/>
        <ul v-if="todos.length">
			<TodoItem
				v-for="todo in todos"
				:key="todo.id"
				:todo="todo"
				@remove="removeTodo"
			/>
		</ul>
		<p v-else>
			No hay tareas en la lista.
		</p>
    </div>
</template>

<script>
import TodoInput from "./TodoInput.vue";
import TodoItem from "./TodoItem.vue";

let todoId = 1;

export default {
  name: "TodoList",
  components: {
    TodoInput,
    TodoItem
  },
  data() {
    return {
      newTodo: "tarea",
      todos: [
        {
          id: todoId++,
          text: "Tarea 1"
        },
        {
          id: todoId++,
          text: "Tarea 2"
        },
        {
          id: todoId++,
          text: "Tarea 3"
        }
      ]
    };
  },
  methods: {
    addTodo() {
      const trimmedText = this.newTodo.trim();
      if (trimmedText) {
        this.todos.push({
          id: todoId++,
          text: trimmedText
        });
        this.newTodo = "";
      }
    },
    removeTodo(idToRemove) {
      this.todos = this.todos.filter(todo => {
        return todo.id !== idToRemove;
      });
    }
  }
};
</script>

<style>
</style>
