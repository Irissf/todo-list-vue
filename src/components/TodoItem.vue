<template>
    <li class="list-group-item d-flex justify-content-between">
        <!-- "{'tachado':todo.estado}" => pinta el css tachado, si todo.estado es igual a true  -->
        <span :class="{'tachado':todo.estado}" role="button" @click="completar(todo.id)">{{todo.texto}}</span> <!--Texto-->
        <span role="button" @click="eliminar(todo.id)"><i class="fas fa-times"></i></span> <!--Icono-->
    </li>
</template>

<script>
import { inject } from '@vue/runtime-core'
export default {
    props:{
        //las buenas prácticas para recoger el prop
        todo:{
            type: Object,
            required: true
        }
    },
    setup(){
        //necesitamos acceder a la lista para eliminar o cambiar el estado
        const todos = inject('todos')

        const eliminar = id =>{
            //cuando el di sea diferente al item.id lo pasamos, si no, pues se va
            todos.value = todos.value.filter(item => item.id !== id)
        }

        const completar = id =>{
            // map retorna un nuebo array con los cambios que queremos añadir
            todos.value = todos.value.map(item => {
                if (item.id === id) {
                    item.estado = true
                }
                return item //tenemos que retornar el item, puesto qeu lo pusimos entre llaves
                //para más operaciones
            })
        }
        return {eliminar,completar}
    }
}
</script>

<style>
.tachado{
    text-decoration: line-through;
}
</style>