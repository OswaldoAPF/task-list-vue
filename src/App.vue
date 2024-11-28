<template>
  <div>
    <input v-model="nuevaTareaTexto" @keyup.enter="agregarTarea" placeholder="Agregar tarea" />
    <ListaTareas :tareas="tareas" @eliminarTarea="eliminarTarea" @actualizarCompletada="actualizarTarea" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ListaTareas from './components/ListaTareas.vue';

const nuevaTareaTexto = ref('');
const tareas = ref([
  { id: 1, texto: 'Tarea 1', completada: false },
  { id: 2, texto: 'Tarea 2', completada: false },
]);

// Agregar tarea nueva
const agregarTarea = () => {
  if (nuevaTareaTexto.value.trim()) {
    tareas.value.push({
      id: Date.now(),
      texto: nuevaTareaTexto.value,
      completada: false,
    });
    nuevaTareaTexto.value = ''; // Limpiar el input después de agregar la tarea
  }
};

// Eliminar tarea
const eliminarTarea = (id) => {
  tareas.value = tareas.value.filter((tarea) => tarea.id !== id);
};

// Actualizar tarea (marcar como completada)
const actualizarTarea = (id) => {
  const tarea = tareas.value.find((tarea) => tarea.id === id);
  if (tarea) {
    tarea.completada = !tarea.completada;
  }
};
</script>

<style>
h1 {
  text-align: center;
  color: #333;
}
</style>