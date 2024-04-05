<script setup>

import Task from "./Task.vue";
import {ref} from 'vue'

const todo = ref([
  {id: 1, tarea: "Aprender Vue.js", hecha: false},
  {id: 2, tarea: "Aprender React", hecha: false},
  {id: 3, tarea: "Comprar el pan", hecha: true}
])
const nuevaTarea = ref("")
const eliminarTareas = ()=>{
  todo.value = todo.value.filter(x => !x.hecha)
}
const addTarea = () => {
  todo.value.push({
    id: todo.value.length+1,
    tarea: nuevaTarea.value,
    hecha: false
  })
  nuevaTarea.value=""
}
</script>

<template>
  <main id="app">
    <article id="todoapp">
      <form @submit.prevent="addTarea" id="form-tarea">
        <input type="text" placeholder="Añade tarea" v-model="nuevaTarea" id="input-text-tarea">
        <button :disabled="nuevaTarea.length < 1 || nuevaTarea.length > 100" type="submit" id="button-tarea">Añadir tarea</button>
      </form>
      <section id="lista">
        <Task
            v-for="item in todo"
            :id="item.id"
            :tarea="item.tarea"
            :hecha="item.hecha"
            :class="{tachado: item.hecha}"
            @click="item.hecha = !item.hecha"
        />
      </section>
    </article>
    <button type="button" id="button-eliminar-tarea" @click="eliminarTareas" :disabled="todo.length < 1" >Eliminar tareas terminadas</button>
  </main>
</template>

<style scoped>
#app{
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
  align-items: center;
  margin: 0;
}
#todoapp{
  display: block;
  text-align: center;
  width: 100%;
  padding: 2vw;
  background-color: #383535;
  border-radius: 10px;
}
.tachado{
  text-decoration: line-through;
  text-decoration-style: solid;
  text-decoration-color: #535bf2;
  background-color: #f34646;
}
#lista {
  display: flex;
  padding: 0;
  margin: 10px 0;
  align-items: center;
  flex-flow: column nowrap;
  list-style-type: none;
}
#form-tarea{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
#input-text-tarea{
  width: 35%;
  background-color: #464242;
  padding: 3px;
}
#input-text-tarea:focus{
  background-color: #343131;
}
#button-tarea {
  padding: 0.3vw 0.6vw;
  width: 35%;
  background-color: #6c6cff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
#button-tarea:hover {
  background-color: #3394f1;
}
#button-tarea:active {
  background-color: #2881da;
}
#button-tarea[disabled] {
  background-color: #a8a8f5;
  cursor: initial;
}
#button-eliminar-tarea {
  margin: 0.3vw;
}
#button-eliminar-tarea:hover{
  background-color: #260000;
}
#button-eliminar-tarea[disabled] {
  background-color: #2a2a2a;
  cursor: initial;
}
</style>