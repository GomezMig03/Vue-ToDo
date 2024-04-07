<script setup>
defineProps({
  id: Number,
  tarea: String,
  hecha: Boolean
})
</script>

<template>
  <section id="task-item">
    <p id="list-item">{{tarea}}</p>
    <button class="done">✔</button>
    <button class="delete"> 🗑️</button>
  </section>
</template>

<style scoped>
#list-item {
  background-color: #3394f1;
  width: 100%;
  margin: 0.3vw;
  border-radius: 5px;
  user-select: none;
}
#list-item:hover{
  cursor:pointer;
}
#task-item{
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-evenly;
  width: 100%;
}
.delete{
  text-decoration: none !important;
  background: red;
}
</style>