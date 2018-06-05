<template>
  <section class="todoapp">
    <header class="header">
      <h1>todos</h1>
      <input class="new-todo" placeholder="What needs to be done?" autofocus>
    </header>
    <!-- This section should be hidden by default and shown when there are todos -->
    <section class="main">
      <input id="toggle-all" class="toggle-all" type="checkbox">
      <label for="toggle-all">Mark all as complete</label>
      <ul class="todo-list">
        <!-- These are here just to show the structure of the list items -->
        <!-- List items should get the class `editing` when editing and `completed` when marked as completed -->
        <li 
          v-for="todo in todos"
          v-bind:key="todo.name"
          v-bind:class="todo.completed ? 'completed' : ''"
        >
          <div class="view">
            <input
              class="toggle" type="checkbox" 
              v-bind:checked="todo.completed"
            />
            <label>{{ todo.name }}</label>
            <button class="destroy"></button>
            <input class="edit" v-bind:value="todo.name" />
          </div>
        </li>
      </ul>
    </section>
    <!-- This footer should hidden by default and shown when there are todos -->
    <footer class="footer">
      <!-- This should be `0 items left` by default -->
      <span class="todo-count"><strong>0</strong> item left</span>
      <!-- Remove this if you don't implement routing -->
      <ul class="filters">
        <li>
          <a class="selected" href="#/">All</a>
        </li>
        <li>
          <a href="#/active">Active</a>
        </li>
        <li>
          <a href="#/completed">Completed</a>
        </li>
      </ul>
      <!-- Hidden if no completed items are left ↓ -->
      <button class="clear-completed">Clear completed</button>
    </footer>
  </section>
</template>

<script>
import '../assets/todomvc-common.css'
import '../assets/todomvc-app.css'

export default {
  name: 'TodoList',
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
    }
  },
}
</script>