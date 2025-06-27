<script setup>
const props = defineProps(['resultado']);
</script>

<template>
     <div class="resultado">
          <p>Resultado:</p>
          <span> {{ props.resultado }}</span>
     </div>
</template>

<style scoped>
.resultado {
     max-width: 300px;
     width: 100%;
     margin: 0 auto;
     margin-top: 15px;
     display: flex;
     flex-direction: column;
     align-items: center;
     background-color: #666666;
     box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
     padding: 20px;
     border-radius: 5px;

     p {
          font-size: 18px;
     }

     span {
          font-size: 24px;
     }
}
</style>
