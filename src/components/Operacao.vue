<script setup>
const props = defineProps(['operacao', 'funcaoCalcular']);
const emit = defineEmits(['update:operacao']);

const onChange = evento => {
     emit('update:operacao', evento.target.value);
     props.funcaoCalcular();
};
</script>

<template>
     <select :value="props.operacao" @change="onChange" class="select">
          <option value="add">Adição</option>
          <option value="sub">Subtração</option>
          <option value="mul">Multiplicação</option>
          <option value="div">Divisão</option>
     </select>
</template>

<style scoped>
.select {
     width: 300px;
     padding: 10px;
     border-radius: 10px;
     margin: 10px 0;
     cursor: pointer;
}
</style>
