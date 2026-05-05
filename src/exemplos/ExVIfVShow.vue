<template>
  <div class="wrap">
    <div class="card">
      <p class="titulo">v-if, v-else e v-show</p>
      <p class="subtitulo">
        Renderização condicional no Vue.
      </p>

      <!-- EXPLICAÇÃO -->
      <section class="bloco destaque">
        <p>
          Esses recursos permitem mostrar ou esconder elementos
          com base no estado da aplicação.
        </p>
      </section>

      <!-- V-IF -->
      <section class="bloco">
        <div class="bloco-header">
          <span class="badge">1</span>
          <h3>v-if / v-else-if / v-else</h3>
        </div>

        <p class="descricao">
          Aqui o Vue renderiza conteúdos diferentes dependendo da nota do aluno.
        </p>

        <input
          v-model.number="nota"
          type="number"
          min="0"
          max="10"
          placeholder="Digite uma nota"
        />

        <div class="resultado">
          <p class="aprovado" v-if="nota >= 7">
            ✅ Aprovado
          </p>

          <p class="recuperacao" v-else-if="nota >= 5">
            ⚠️ Recuperação
          </p>

          <p class="reprovado" v-else>
            ❌ Reprovado
          </p>
        </div>
      </section>

      <!-- V-SHOW -->
      <section class="bloco">
        <div class="bloco-header">
          <span class="badge">2</span>
          <h3>v-show</h3>
        </div>

        <p class="descricao">
          Diferente do <code>v-if</code>, o elemento continua existindo
          no DOM, apenas fica oculto visualmente.
        </p>

        <button
          class="btn-primary"
          @click="mostrar = !mostrar"
        >
          {{ mostrar ? 'Ocultar mensagem' : 'Mostrar mensagem' }}
        </button>

        <div
          class="mensagem"
          v-show="mostrar"
        >
          👀 Esta mensagem usa <strong>v-show</strong>.
        </div>

        <p class="estado-dom">
          DOM:
          <strong>
            {{ mostrar ? 'Elemento visível' : 'Elemento oculto (mas ainda existe)' }}
          </strong>
        </p>
      </section>
    </div>
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
  border: 1px solid #e0e0de;
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

.destaque {
  background: #eef8f4;
}

.bloco-header {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 12px;
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
}

.descricao {
  font-size: 13px;
  color: #888780;
  margin-bottom: 1rem;
  line-height: 1.5;
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
  transition: .2s;
}

input:focus {
  border-color: #1D9E75;
  box-shadow: 0 0 0 3px rgba(29,158,117,.12);
}

.resultado {
  margin-top: 14px;
  padding: 14px;
  border-radius: 10px;
  background: white;
  border: 1px solid #ecebe7;
}

.aprovado {
  color: #1D9E75;
  font-weight: 600;
}

.recuperacao {
  color: #c78300;
  font-weight: 600;
}

.reprovado {
  color: #c43838;
  font-weight: 600;
}

.btn-primary {
  width: 100%;
  height: 42px;
  border: none;
  border-radius: 8px;
  background: #1D9E75;
  color: white;
  font-size: 14px;
  cursor: pointer;
  transition: .2s;
}

.btn-primary:hover {
  background: #0F6E56;
}

.mensagem {
  margin-top: 14px;
  padding: 12px;
  border-radius: 8px;
  background: #eef8f4;
}

.estado-dom {
  margin-top: 12px;
  font-size: 13px;
  color: #666;
}

code {
  background: white;
  padding: 2px 6px;
  border-radius: 4px;
}
</style>