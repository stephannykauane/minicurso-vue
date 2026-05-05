<template>
  <div class="wrap">
    <div class="card">
      <p class="titulo">Interpolação e v-model</p>
      <p class="subtitulo">
        Entendendo renderização dinâmica e ligação bidirecional de dados.
      </p>

      <!-- Interpolação -->
      <section class="bloco">
        <div class="bloco-header">
          <span class="badge">1</span>
          <h3>Interpolação</h3>
        </div>

        <p class="descricao">
          O Vue permite exibir valores dinâmicos diretamente no HTML com
          chaves duplas.
        </p>

        <div class="codigo-preview">
          <div class="linha">
            <span class="label">Mensagem:</span>
            <strong>{{ mensagem }}</strong>
          </div>

          <div class="linha">
            <span class="label">Expressão:</span>
            <strong>{{ 2 + 2 }}</strong>
          </div>

          <div class="linha">
            <span class="label">Objeto:</span>
            <strong>{{ usuario.nome }}</strong>
          </div>
        </div>
      </section>

      <!-- V-MODEL -->
      <section class="bloco">
        <div class="bloco-header">
          <span class="badge">2</span>
          <h3>v-model</h3>
        </div>

        <p class="descricao">
          O <code>v-model</code> cria uma ligação bidirecional entre o input e os dados.
        </p>

        <input
          v-model="nome"
          placeholder="Digite seu nome..."
        />

        <div class="feedback" v-if="nome">
          👋 Olá,
          <strong>{{ nome }}</strong>
        </div>

        <div class="estado-vazio" v-else>
          Digite algo acima para ver a reatividade em ação.
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mensagem: "Olá, Mundo!",
      usuario: {
        nome: "Vue.js"
      },
      nome: ""
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
  justify-content: center;
  padding: 3rem 1rem;
  background: #f5f5f3;
  font-family: 'Inter', sans-serif;
}

.card {
  width: 100%;
  max-width: 700px;
  background: white;
  border: 0.5px solid #e0e0de;
  border-radius: 16px;
  padding: 2rem;
}

.titulo {
  font-size: 24px;
  font-weight: 600;
  color: #1a1a18;
}

.subtitulo {
  margin-top: 4px;
  margin-bottom: 2rem;
  font-size: 14px;
  color: #888780;
}

.bloco {
  padding: 1.5rem;
  border: 1px solid #ecebe7;
  border-radius: 12px;
  background: #fafaf9;
  margin-bottom: 1.25rem;
}

.bloco-header {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}

.badge {
  width: 24px;
  height: 24px;
  border-radius: 50%;
  background: #1D9E75;
  color: white;
  font-size: 12px;
  font-weight: 600;

  display: flex;
  align-items: center;
  justify-content: center;
}

h3 {
  font-size: 16px;
  color: #1a1a18;
}

.descricao {
  font-size: 13px;
  color: #888780;
  margin-bottom: 1rem;
  line-height: 1.5;
}

.codigo-preview {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.linha {
  padding: 12px;
  background: white;
  border: 1px solid #ecebe7;
  border-radius: 8px;
  font-size: 14px;
}

.label {
  color: #888780;
  margin-right: 6px;
}

input {
  width: 100%;
  height: 42px;
  padding: 0 14px;
  border: 0.5px solid #c8c7c0;
  border-radius: 8px;
  background: white;
  font-size: 14px;
  outline: none;
  transition: 0.2s;
}

input:focus {
  border-color: #1D9E75;
  box-shadow: 0 0 0 3px rgba(29,158,117,.12);
}

.feedback {
  margin-top: 14px;
  padding: 12px;
  background: #eef8f4;
  border-radius: 8px;
  font-size: 14px;
}

.estado-vazio {
  margin-top: 14px;
  padding: 12px;
  background: #f8f8f7;
  border-radius: 8px;
  color: #888780;
  font-size: 13px;
}

code {
  background: #f1f1ef;
  padding: 2px 6px;
  border-radius: 4px;
  font-size: 12px;
}
</style>