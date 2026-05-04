<template>
  <div class="exemplo">
    <h2>v-for — Renderização de listas</h2>

    <!-- v-for com array de strings -->
    <h3>Lista de frutas</h3>
    <ul>
      <li v-for="(item, index) in frutas" :key="index">
        {{ index + 1 }} - {{ item }}
      </li>
    </ul>

    <!-- v-for com array de objetos -->
    <h3>Lista de produtos</h3>
    <ul>
      <li v-for="produto in produtos" :key="produto.id">
        {{ produto.nome }} — R$ {{ produto.preco.toFixed(2) }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      frutas: ["Maçã", "Banana", "Uva"],
      produtos: [
        { id: 1, nome: "Teclado", preco: 129.9 },
        { id: 2, nome: "Mouse",   preco: 79.9  },
        { id: 3, nome: "Monitor", preco: 899.0 }
      ]
    }
  }
}
</script>

<style scoped>
.exemplo { font-family: Arial, sans-serif; padding: 16px; }
ul { padding-left: 20px; }
li { margin-bottom: 4px; }
h3 { margin-top: 16px; color: #333; }
</style>