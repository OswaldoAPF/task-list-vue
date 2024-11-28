<template>
  <li>
    <input type="checkbox" :checked="tarea.completada" @change="toggleCompletada" />
    <span :class="{ completada: tarea.completada }">{{ tarea.texto }}</span>
    <button @click="eliminar">x</button>
  </li>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  tarea: Object,
});

const emit = defineEmits(['eliminarTarea', 'actualizarCompletada']);

const toggleCompletada = () => {
  emit('actualizarCompletada', props.tarea.id);
};

const eliminar = () => {
  emit('eliminarTarea', props.tarea.id);
};
</script>

<style scoped>
.completada {
  text-decoration: line-through;
  color: #888;
}
</style>