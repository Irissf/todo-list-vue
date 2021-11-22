<template>
    <div>
        <h1>ToDo-List</h1> 
        <todo-form />
        <todo-list/>
    </div> 
</template>

<script>
import {ref,provide, watchEffect} from 'vue'
import TodoForm from './TodoForm.vue'
import TodoList from './TodoList.vue'
export default {
    components: { TodoForm, TodoList },
    //Composition API, lo nuevo de vue 3, lo ponemos en el padre, apra que accedan los hijos
    setup(){
        //variables reactivas, podemos hacerlos con ref o reactive, pero la segunda es más compleja
        const todos = ref([])
        //para pasar los todos al formulario, nombre para referenciar, y segundo param el valor
        provide('todos',todos) 

        //Está pendiente de lo que le digamos que esté pendiente
        watchEffect(()=>{
            //al poner aqui los todos, watchEffect entiende que tiene que hacerles seguimiento
            console.log(todos.value.length)
            console.log(todos.value)
        })
    }
        
}
</script>

<style>

</style>