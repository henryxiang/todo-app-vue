<template>
  <section class="todoapp">
    <header class="header">
      <h1>todos</h1>
      <input 
        class="new-todo" placeholder="What needs to be done?" autofocus 
        v-model="nextItem" 
        @keyup.enter="addTodo"
      />
    </header>
    <!-- This section should be hidden by default and shown when there are todos -->
    <section class="main">
      <input id="toggle-all" class="toggle-all" type="checkbox">
      <label for="toggle-all">Mark all as complete</label>
      <ul class="todo-list">
        <!-- These are here just to show the structure of the list items -->
        <!-- List items should get the class `editing` when editing and `completed` when marked as completed -->
        <TodoItem 
          v-for="todo in filteredTodos"
          :key="todo.name"
          :todo="todo"
          @delete="deleteTodo"
          @toggle="toggleTodo"
        />
      </ul>
      <!-- <TodoItem :todo="Object.assign(todos[0])" /> -->
    </section>
    <!-- This footer should hidden by default and shown when there are todos -->
    <footer class="footer">
      <!-- This should be `0 items left` by default -->
      <span class="todo-count"><strong>{{ completedTodos }}</strong> item left</span>
      <!-- Remove this if you don't implement routing -->
      <ul class="filters">
        <li>
          <a 
            href="#/all"
            :class="includedStatus === 'all' ? 'selected' : ''"  
            @click="setStatusFilter($event, 'all')"
          >
            All
          </a>
        </li>
        <li>
          <a 
            href="#/active"
            :class="includedStatus === 'active' ? 'selected' : ''"  
            @click="setStatusFilter($event, 'active')"
          >
            Active
          </a>
        </li>
        <li>
          <a 
            href="#/completed"
            :class="includedStatus === 'completed' ? 'selected' : ''"  
            @click="setStatusFilter($event, 'completed')"
          >
            Completed
          </a>
        </li>
      </ul>
      <!-- Hidden if no completed items are left ↓ -->
      <button
        class="clear-completed"
        @click="clearCompleted"
      >
        Clear completed
      </button>
    </footer>
  </section>
</template>

<script>
import '../assets/todomvc-common.css'
import '../assets/todomvc-app.css'
import TodoItem from './TodoItem.vue'

export default {
  name: 'TodoList',
  components: {
    TodoItem,
  },
  data() {
    return {
      todos: [
        {
          name: 'Taste JavaScript',
          completed: true,
        },
        {
          name: 'Buy a unicorn',
          completed: false,
        },
        {
          name: 'Learn Vue.js',
          completed: false,
        },
      ],
      nextItem: '',
      includedStatus: '',
    }
  },
  methods: {
    addTodo() {
      this.todos.push({
        name: this.nextItem,
        completed: false,
      });
      this.nextItem = '';
    },
    deleteTodo(todo) {
      const index = this.todos.map((t) => t.name).indexOf(todo.name);
      this.todos.splice(index, 1);
    },
    toggleTodo(todo) {
      const index = this.todos
            .map((t) => t.name)
            .indexOf(todo.name);
      const t = this.todos[index];
      t.completed = !t.completed;
      this.todos[index] = t;
    },
    setStatusFilter(event, includedStatus) {
      this.includedStatus = includedStatus;
    },
    clearCompleted() {
      this.todos = this.todos.filter((t) => !t.completed);
    },
  },
  computed: {
    completedTodos() {
      return this.todos.filter((t) => !t.completed).length;
    },
    filteredTodos() {
      switch (this.includedStatus) {
        case 'active':
          return this.todos.filter((t) => !t.completed);
        case 'completed':
          return this.todos.filter((t) => t.completed);
        default:
          return this.todos;
      }
    },
  },
}
</script>