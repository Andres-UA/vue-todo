<template>
    <div>
        <TodoInput 
			v-model="newTodo"
			placeholder="Nueva tarea"
			@keydown.enter="saveTodo"
		/>

        <br>
        <br>

        <div class="siimple-list " v-if="todos.length">
			<TodoItem        
				v-for="todo in todos"
				:key="todo.id"
				:todo="todo"
				@remove="removeTodo"
                @edit="editTodo"
			/>
		</div>
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
      newTodo: "",
      idEdit: 0,
      todos: [
        {
          id: todoId++,
          text: "Tarea 1"
        },
        {
          id: todoId++,
          text: "Tarea 2"
        }
      ]
    };
  },
  methods: {
    saveTodo() {
      if (this.idEdit === 0) {
        this.addTodo();
      } else {
        const index = this.todos.findIndex(item => item.id == this.idEdit);

        this.todos.splice(index, 1, {
          id: this.idEdit,
          text: this.newTodo
        });
        this.idEdit = 0;
        this.newTodo = "";
      }
    },
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
    editTodo(idToEdit) {
      let todo = this.todos.filter(todo => {
        return todo.id === idToEdit;
      });
      this.newTodo = todo[0].text;
      this.idEdit = todo[0].id;
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
