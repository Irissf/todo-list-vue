<template>
    <div>
        <ul class="list-group">
            <!-- :todo="todo" =>le mandamos el objeto, un prop -->
            <todo-item v-for="todo in todos" :key="todo.id" :todo="todo"/>
        </ul>
        <!-- Lo usamos cuando hay algún item -->
        <todo-footer v-if="todos.length !== 0"/>
    </div>
</template>

<script>
import { computed, inject } from '@vue/runtime-core'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
export default {
    components: { TodoItem, TodoFooter},
    setup(){
        const todos = inject('todos') //cogemos la lista del padre

        return {todos}
    }
}
</script>

<style>

</style>