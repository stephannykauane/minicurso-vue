<template>
  <div class="wrap">
    <div class="card">
      <p class="titulo">v-bind</p>
      <p class="subtitulo">
        Ligando atributos HTML de forma dinâmica com Vue.
      </p>

      <!-- IMAGENS -->
      <section class="bloco">
        <div class="bloco-header">
          <span class="badge">1</span>
          <h3>Binding de atributos</h3>
        </div>

        <p class="descricao">
          O <code>v-bind</code> permite conectar atributos HTML aos dados do componente.
        </p>

        <div class="preview-imagens">
          <div class="imagem-box">
            <span class="legenda">Forma completa</span>
            <img
              v-bind:src="urlDaImagem"
              v-bind:alt="descricao"
            />
          </div>

          <div class="imagem-box">
            <span class="legenda">Forma abreviada</span>
            <img
              :src="urlDaImagem"
              :alt="descricao"
            />
          </div>
        </div>
      </section>

      <!-- BOTÃO DINÂMICO -->
      <section class="bloco">
        <div class="bloco-header">
          <span class="badge">2</span>
          <h3>Estado dinâmico</h3>
        </div>

        <p class="descricao">
          Também podemos controlar propriedades como
          <code>disabled</code> dinamicamente.
        </p>

        <input
          v-model="texto"
          placeholder="Digite algo para habilitar..."
        />

        <button
          class="btn-primary"
          :disabled="texto.trim() === ''"
        >
          Enviar
        </button>

        <div class="feedback" v-if="texto.trim()">
          Botão habilitado.
        </div>

        <div class="estado-vazio" v-else>
          Digite algo acima para ativar o botão.
        </div>
      </section>
    </div>
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

.preview-imagens {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
}

.imagem-box {
  flex: 1;
  min-width: 180px;
  padding: 1rem;
  background: white;
  border: 1px solid #ecebe7;
  border-radius: 10px;
  text-align: center;
}

.legenda {
  display: block;
  font-size: 12px;
  color: #888780;
  margin-bottom: 10px;
}

img {
  width: 70px;
  height: 70px;
  object-fit: contain;
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
  margin-bottom: 12px;
}

input:focus {
  border-color: #1D9E75;
  box-shadow: 0 0 0 3px rgba(29,158,117,.12);
}

.btn-primary {
  width: 100%;
  height: 42px;
  border: none;
  border-radius: 8px;
  background: #1D9E75;
  color: white;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: .2s;
}

.btn-primary:hover:not(:disabled) {
  background: #0F6E56;
}

.btn-primary:disabled {
  background: #d8d8d4;
  cursor: not-allowed;
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