<template>
  <div class="wrap">
    <div class="card">
      <p class="titulo">Lista de tarefas</p>
      <p class="subtitulo">Organize seu dia de forma simples</p>

      <!-- Campo de entrada + botão -->
      <div class="entrada">
        <input
          v-model="novoItem"
          type="text"
          placeholder="Adicionar nova tarefa..."
          @keyup.enter="adicionarItem"
        />
        <button class="btn-add" @click="adicionarItem">+ Adicionar</button>
      </div>

      <!-- Contador de tarefas -->
      <div v-if="itens.length > 0" class="contador">
        <span class="dot"></span>
        <span>{{ itens.filter(i => i.feita).length }} de {{ itens.length }} concluída{{ itens.length > 1 ? 's' : '' }}</span>
      </div>

      <!-- Mensagem de lista vazia -->
      <div v-if="itens.length === 0" class="vazia">
        <div class="vazia-icon">✓</div>
        <p>Nenhuma tarefa por enquanto.</p>
        <p class="vazia-sub">Adicione algo acima para começar!</p>
      </div>

      <!-- Lista de tarefas -->
      <ul v-else>
        <li
          v-for="(item, index) in itens"
          :key="index"
          :class="{ concluida: item.feita }"
        >
          <div class="check-wrap">
            <input type="checkbox" v-model="item.feita" />
          </div>
          <span class="texto">{{ item.texto }}</span>
          <button class="btn-rem" @click="removerItem(index)" title="Remover">✕</button>
        </li>
      </ul>
    </div>
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
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.wrap {
  min-height: 100vh;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  padding: 3rem 1rem;
  font-family: 'Inter', Arial, sans-serif;
  background-color: #f5f5f3;
}

.card {
  width: 100%;
  max-width: 520px;
  background: #ffffff;
  border: 0.5px solid #e0e0de;
  border-radius: 16px;
  padding: 2rem;
}

.titulo {
  font-size: 22px;
  font-weight: 500;
  color: #1a1a18;
  margin-bottom: 4px;
}

.subtitulo {
  font-size: 13px;
  color: #888780;
  margin-bottom: 1.75rem;
}

/* ── Campo de entrada ── */
.entrada {
  display: flex;
  gap: 10px;
  margin-bottom: 1.25rem;
}

.entrada input {
  flex: 1;
  height: 42px;
  padding: 0 14px;
  border: 0.5px solid #c8c7c0;
  border-radius: 8px;
  font-size: 14px;
  font-family: inherit;
  background: #f5f5f3;
  color: #1a1a18;
  outline: none;
  transition: border-color 0.15s, box-shadow 0.15s;
}

.entrada input:focus {
  border-color: #1D9E75;
  box-shadow: 0 0 0 3px rgba(29, 158, 117, 0.12);
}

.entrada input::placeholder {
  color: #b4b2a9;
}

.btn-add {
  height: 42px;
  padding: 0 18px;
  background: #1D9E75;
  color: #ffffff;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 500;
  font-family: inherit;
  cursor: pointer;
  white-space: nowrap;
  transition: background 0.15s, transform 0.1s;
}

.btn-add:hover {
  background: #0F6E56;
}

.btn-add:active {
  transform: scale(0.97);
}

/* ── Contador ── */
.contador {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 12px;
  color: #888780;
  margin-bottom: 1rem;
}

.dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #1D9E75;
  display: inline-block;
  flex-shrink: 0;
}

/* ── Estado vazio ── */
.vazia {
  text-align: center;
  padding: 3rem 1rem;
  color: #b4b2a9;
  font-size: 14px;
}

.vazia-icon {
  font-size: 36px;
  margin-bottom: 10px;
}

.vazia-sub {
  margin-top: 4px;
  font-size: 12px;
}

/* ── Lista ── */
ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

li {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px 14px;
  background: #f5f5f3;
  border: 0.5px solid #e0e0de;
  border-radius: 8px;
  transition: opacity 0.2s;
}

li:hover .btn-rem {
  opacity: 1;
}

li.concluida {
  opacity: 0.55;
}

/* ── Checkbox customizado ── */
.check-wrap {
  position: relative;
  flex-shrink: 0;
}

.check-wrap input[type="checkbox"] {
  appearance: none;
  -webkit-appearance: none;
  width: 18px;
  height: 18px;
  border: 1.5px solid #c8c7c0;
  border-radius: 4px;
  cursor: pointer;
  transition: background 0.15s, border-color 0.15s;
}

.check-wrap input[type="checkbox"]:checked {
  background: #1D9E75;
  border-color: #1D9E75;
}

.check-wrap input[type="checkbox"]:checked::after {
  content: '';
  position: absolute;
  left: 5px;
  top: 2px;
  width: 5px;
  height: 9px;
  border: 2px solid #ffffff;
  border-top: none;
  border-left: none;
  transform: rotate(45deg);
}

/* ── Texto da tarefa ── */
.texto {
  flex: 1;
  font-size: 14px;
  color: #1a1a18;
  line-height: 1.4;
  transition: color 0.2s;
}

li.concluida .texto {
  text-decoration: line-through;
  color: #b4b2a9;
}

/* ── Botão remover ── */
.btn-rem {
  flex-shrink: 0;
  width: 28px;
  height: 28px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: none;
  background: transparent;
  cursor: pointer;
  border-radius: 6px;
  color: #888780;
  font-size: 14px;
  opacity: 0;
  transition: background 0.15s, color 0.15s, opacity 0.15s;
}

.btn-rem:hover {
  background: #FCEBEB;
  color: #A32D2D;
}
</style>