<template>
  <div class="exemplo">
    <h2>v-bind — Atributos dinâmicos</h2>

    <!-- Forma completa -->
    <img v-bind:src="urlDaImagem" v-bind:alt="descricao" width="100" />

    <!-- Forma abreviada (preferida) -->
    <img :src="urlDaImagem" :alt="descricao" width="100" />

    <!-- Desabilitar botão dinamicamente -->
    <input v-model="texto" placeholder="Digite algo para habilitar o botão" />
    <button :disabled="texto.trim() === ''">Enviar</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      urlDaImagem: "https://vuejs.org/images/logo.png",
      descricao: "Logo do Vue.js",
      texto: ""
    }
  }
}
</script>

<style scoped>
.exemplo { 
font-family: Arial, sans-serif; 
padding: 16px; }
input { 
padding: 8px; border: 1px solid #ccc;
 border-radius: 4px; 
 margin-right: 8px; }
button { padding: 8px 14px; background-color: #42b883; color: white; border: none; border-radius: 4px; cursor: pointer; }
button:disabled { background-color: #ccc; cursor: not-allowed; }
img { display: block; margin-bottom: 12px; }
</style>