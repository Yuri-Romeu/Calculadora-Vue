<script setup>
const props = defineProps(['funcaoCalcular', 'primeiroNumero', 'segundoNumero']);
const emit = defineEmits(['update:primeiroNumero', 'update:segundoNumero']);
</script>

<template>
     <input
          :value="props.primeiroNumero"
          @input="
               evento => {
                    emit('update:primeiroNumero', evento.target.value);
                    props.funcaoCalcular();
               }
          "
          type="number"
          placeholder="Escolha um número"
     />
     <input
          :value="props.segundoNumero"
          @input="
               evento => {
                    emit('update:segundoNumero', evento.target.value);
                    props.funcaoCalcular();
               }
          "
          type="number"
          placeholder="Escolha outro número"
     />
</template>

<style scoped>
input {
     padding: 10px;
     border-radius: 10px;
     color: #000;
     border: none;
     width: 300px;
     margin: 10px 0;
}
</style>
