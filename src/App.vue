<template>
  <div class="container">
    <h1>Task List</h1>
    <input type="text" v-model="nuevaTareaTexto" @keyup.enter="agregarTarea" placeholder="Add Task" />
    <ListaTareas :tareas="tareas" @eliminarTarea="eliminarTarea" @actualizarCompletada="actualizarTarea" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ListaTareas from './components/ListaTareas.vue';
import './assets/main.css';

const nuevaTareaTexto = ref('');
const tareas = ref([]);

const agregarTarea = () => {
  if (nuevaTareaTexto.value.trim()) {
    tareas.value.push({
      id: Date.now(),
      texto: nuevaTareaTexto.value,
      completada: false,
    });
    nuevaTareaTexto.value = '';
  }
};

const eliminarTarea = (id) => {
  tareas.value = tareas.value.filter((tarea) => tarea.id !== id);
};

const actualizarTarea = (id) => {
  const tarea = tareas.value.find((tarea) => tarea.id === id);
  if (tarea) {
    tarea.completada = !tarea.completada;
  }
};
</script>