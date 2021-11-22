<template>
  <form @submit.prevent="formulario">
      <!-- Con v-model.trim ya quitamos los espacios de los bordes -->
      <input type="text" class="form-control my-3" placeholder="Ingresar tarea" v-model.trim="texto">
  </form>
</template>

<script>
import { inject,ref } from '@vue/runtime-core'
export default {
    setup(){
        //recogemos el valor que queremos del padre Composer API con inject
        const todos = inject('todos') //param el nombre de referencia que pusimos
        const texto = ref('') // este lo declaramos aqui, no lo necesitamos en otros componentes
        
        const formulario = ()=>{
            //validamos que no esté vacio el texto
            if (texto.value === '') {
                console.log('está vacio')
                return // si no hay texto sale y no sigue
            }

            //creamos un objeto todo con el texto, id y estado
            const todo = {
                texto: texto.value,
                estado: false, //se genera sin completar
                id: Date.now() //no tira la fecha y hora de creares, asi el id es unico y se autogera
            }
            todos.value.push(todo);//lo metemos en el array
            texto.value='' //reiniciamos el texto
        } 

        return{formulario,texto} //retornamos todo para poder usar las funciones del setup
    }
}
</script>

<style>

</style>