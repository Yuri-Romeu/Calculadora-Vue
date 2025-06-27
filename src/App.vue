<script setup>
import { reactive } from 'vue';
import Inputs from './components/Inputs.vue';
import Operacao from './components/Operacao.vue';
import Resultado from './components/Resultado.vue';

const estado = reactive({
     primeiroNumero: 0,
     segundoNumero: 0,
     operacao: 'add',
     resultado: 0,
});

const calcular = () => {
     if (estado.primeiroNumero === '' || estado.segundoNumero === '') {
          estado.resultado = 0;
          return;
     }

     const num1 = Number(estado.primeiroNumero);
     const num2 = Number(estado.segundoNumero);

     if (isNaN(num1) || isNaN(num2)) {
          estado.resultado = 0;
          return;
     }

     if (estado.operacao === 'div' && num2 === 0) {
          estado.resultado = 'Erro';
          return;
     }

     switch (estado.operacao) {
          case 'sub':
               estado.resultado = num1 - num2;
               break;
          case 'mul':
               estado.resultado = num1 * num2;
               break;
          case 'div':
               estado.resultado = num1 / num2;
               break;
          default: // add
               estado.resultado = num1 + num2;
               break;
     }

     if (estado.resultado === 'infinity') {
          estado.resultado = 'Não é possivel dividir por 0';
     }
};
</script>

<template>
     <div class="container">
          <div class="row">
               <h1 class="title">Calculadora Aritmética</h1>
               <form class="form">
                    <Inputs
                         :funcao-calcular="calcular"
                         v-model:primeiroNumero="estado.primeiroNumero"
                         v-model:segundoNumero="estado.segundoNumero"
                    />

                    <Operacao :funcao-calcular="calcular" v-model:operacao="estado.operacao" />
               </form>

               <Resultado :resultado="estado.resultado" />
          </div>
     </div>
</template>

<style scoped>
.container {
     display: flex;
     align-items: center;
     flex-direction: column;
     padding-top: 50px;
}

.title {
     text-align: center;
     margin: 10px 0;
     font-size: 50px;
}

.form {
     text-align: center;
     display: flex;
     align-items: center;
     flex-direction: column;
}
</style>
