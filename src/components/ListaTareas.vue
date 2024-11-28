<template>
  <ul>
    <TareaItem
      v-for="tarea in tareas"
      :key="tarea.id"
      :tarea="tarea"
      @eliminarTarea="eliminarTarea"
      @actualizarCompletada="actualizarTarea"
    />
  </ul>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
import TareaItem from './TareaItem.vue';

const props = defineProps({
  tareas: Array,
});

const emit = defineEmits(['eliminarTarea', 'actualizarCompletada']);

const eliminarTarea = (id) => {
  emit('eliminarTarea', id);
};

const actualizarTarea = (id) => {
  emit('actualizarCompletada', id);
};
</script>