<template>
  <div class="container">
    <h2>Lista de Tarefas</h2>

    <!-- Campo de entrada + botão -->
    <div class="entrada">
      <input
        v-model="novoItem"
        placeholder="Digite uma tarefa..."
        @keyup.enter="adicionarItem"
      />
      <button @click="adicionarItem">Adicionar</button>
    </div>

    <!-- Mensagem de lista vazia -->
    <p v-if="itens.length === 0" class="vazia">
      Nenhuma tarefa adicionada ainda.
    </p>

    <!-- Lista de tarefas -->
    <ul v-else>
      <li
        v-for="(item, index) in itens"
        :key="index"
        :class="{ concluida: item.feita }"
      >
        <input type="checkbox" v-model="item.feita" />
        <span>{{ item.texto }}</span>
        <button @click="removerItem(index)">Remover</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      novoItem: "",  // texto digitado pelo usuário
      itens: []      // lista de tarefas (começa vazia)
    }
  },
  methods: {
    adicionarItem() {
      // Só adiciona se o campo não estiver vazio
      if (this.novoItem.trim() !== "") {
        this.itens.push({
          texto: this.novoItem.trim(),
          feita: false
        })
        this.novoItem = "" // limpa o campo após adicionar
      }
    },
    removerItem(index) {
      // Remove o item na posição "index" do array
      this.itens.splice(index, 1)
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: 40px auto;
  font-family: Arial, sans-serif;
}

.entrada {
  display: flex;
  gap: 8px;
  margin-bottom: 16px;
}

input[type="text"],
input:not([type]) {
  padding: 8px;
  flex: 1;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 8px 14px;
  background-color: #42b883;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #33a06f;
}

ul {
  margin-top: 16px;
  padding-left: 0;
  list-style: none;
}

li {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 8px;
  border-bottom: 1px solid #ddd;
}

li.concluida span {
  text-decoration: line-through;
  color: #999;
}

.vazia {
  text-align: center;
  color: #888;
}
</style>