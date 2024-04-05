<script setup>
defineProps({
  id: Number,
  tarea: String,
  hecha: Boolean
})
</script>

<template>
  <p id="list-item">{{tarea}}</p>
</template>

<style scoped>
#list-item {
  background-color: #3394f1;
  width: 80%;
  margin: 0.3vw;
  border-radius: 5px;
  user-select: none;
}
#list-item:hover{
  cursor:pointer;
}
</style>