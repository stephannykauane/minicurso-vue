<template>
  <div class="exemplo">
    <h2>v-if / v-else / v-show — Renderização condicional</h2>

    <!-- v-if / v-else-if / v-else -->
    <label>Nota: <input v-model.number="nota" type="number" min="0" max="10" /></label>
    <p v-if="nota >= 7" class="aprovado">Aprovado</p>
    <p v-else-if="nota >= 5" class="recuperacao">Recuperação</p>
    <p v-else class="reprovado">Reprovado</p>

    <hr />

    <!-- v-show: oculta com display:none, elemento permanece no DOM -->
    <button @click="mostrar = !mostrar">
      {{ mostrar ? 'Ocultar' : 'Mostrar' }} mensagem
    </button>
    <p v-show="mostrar" class="destaque">
      Esta mensagem usa v-show — ela permanece no DOM mesmo oculta!
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nota: 7,
      mostrar: true
    }
  }
}
</script>

<style scoped>
.exemplo { font-family: Arial, sans-serif; padding: 16px; }
input[type="number"] { width: 60px; padding: 4px; margin-left: 8px; }
.aprovado    { color: green; font-weight: bold; }
.recuperacao { color: orange; font-weight: bold; }
.reprovado   { color: red; font-weight: bold; }
.destaque    { background: #e8f5e9; padding: 8px; border-radius: 4px; }
button { padding: 8px 14px; background-color: #42b883; color: white; border: none; border-radius: 4px; cursor: pointer; margin-top: 8px; }
hr { margin: 16px 0; }
</style>