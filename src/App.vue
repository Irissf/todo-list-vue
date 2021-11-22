<template>
  <div class="container">
    <!-- Llamamos al componente TodoApp -->
    <todo-app/>
  </div>
</template>

<script>
import TodoApp from './components/TodoApp.vue'


export default {
  components: { TodoApp },
  name: 'App',
}
</script>

