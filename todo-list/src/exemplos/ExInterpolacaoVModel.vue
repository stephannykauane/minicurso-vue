<template>
  <div class="exemplo">
    <h2>Interpolação e v-model</h2>

    <!-- Interpolação simples -->
    <p>{{ mensagem }}</p>
    <p>{{ 2 + 2 }}</p>
    <p>{{ usuario.nome }}</p>

    <!-- v-model: ligação bidirecional -->
    <input v-model="nome" placeholder="Digite seu nome" />
    <p>Olá, {{ nome }}!</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mensagem: "Olá, Mundo!",
      usuario: { nome: "Vue.js" },
      nome: ""
    }
  }
}
</script>

<style scoped>
.exemplo { font-family: Arial, sans-serif; padding: 16px; }
input { padding: 8px; border: 1px solid #ccc; border-radius: 4px; }
</style>