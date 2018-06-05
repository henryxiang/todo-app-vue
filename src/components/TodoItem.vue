<template>
  <li :class="todo.completed ? 'completed' : ''">
    <div class="view">
      <input
        class="toggle" type="checkbox"
        :checked="todo.completed"
        @change="$emit('toggle', todo)"
      />
      <label>{{ todo.name }}</label>
      <button 
        class="destroy" 
        @click="$emit('delete', todo)"
      />
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
