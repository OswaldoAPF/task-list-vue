<template>
  <li>
    <input type="checkbox" :checked="tarea.completada" @change="toggleCompletada" />
    <span :class="{ completada: tarea.completada }">{{ tarea.texto }}</span>
    <button @click="eliminar">Eliminar</button>
  </li>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

// Recibir tarea y métodos como props
const props = defineProps({
  tarea: Object,
});

const emit = defineEmits(['eliminarTarea', 'actualizarCompletada']);

// Método para actualizar el estado de la tarea (completada)
const toggleCompletada = () => {
  emit('actualizarCompletada', props.tarea.id);
};

// Método para eliminar la tarea
const eliminar = () => {
  emit('eliminarTarea', props.tarea.id);
};
</script>

<style scoped>
/* Estilo para el texto de las tareas completadas */
.completada {
  text-decoration: line-through;
  color: #888; /* O cualquier color que desees */
}
</style>