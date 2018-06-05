<template>
  <li :class="todo.completed ? 'completed' : ''">
    <div class="view">
      <input
        class="toggle" type="checkbox"
        :checked="todo.completed"
      />
      <label>{{ todo.name }}</label>
      <button class="destroy"></button>
    </div>
  </li>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    todo: Object,
  },
}
</script>
