<template>
  <div class="wrap">
    <div class="card">
      <p class="titulo">Eventos no Vue</p>
      <p class="subtitulo">
        Exemplos práticos com @click, @keyup e @submit
      </p>

      <!-- CLICK -->
      <section class="bloco">
        <div class="bloco-header">
          <span class="badge">1</span>
          <h3>@click</h3>
        </div>

        <p class="descricao">
          Atualizando valores através de interação com botão.
        </p>

        <button class="btn-primary" @click="incrementar">
          + Clique aqui
        </button>

        <div class="resultado">
          <span class="label">Cliques:</span>
          <strong>{{ contador }}</strong>
        </div>
      </section>

      <!-- KEYUP -->
      <section class="bloco">
        <div class="bloco-header">
          <span class="badge">2</span>
          <h3>@keyup.enter</h3>
        </div>

        <p class="descricao">
          Capturando o Enter após digitar.
        </p>

        <input
          v-model="consulta"
          placeholder="Digite algo e pressione Enter..."
          @keyup.enter="buscar"
        />

        <div v-if="resultado" class="feedback">
          🔍 Buscando por:
          <strong>{{ resultado }}</strong>
        </div>
      </section>

      <!-- SUBMIT -->
      <section class="bloco">
        <div class="bloco-header">
          <span class="badge">3</span>
          <h3>@submit.prevent</h3>
        </div>

        <p class="descricao">
          Enviando formulários sem recarregar a página.
        </p>

        <form @submit.prevent="enviar" class="form-area">
          <input
            v-model="nomeForm"
            placeholder="Digite seu nome..."
          />

          <button type="submit" class="btn-primary">
            Enviar
          </button>
        </form>

        <div v-if="enviado" class="feedback success">
          Formulário enviado por:
          <strong>{{ enviado }}</strong>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contador: 0,
      consulta: "",
      resultado: "",
      nomeForm: "",
      enviado: ""
    }
  },

  methods: {
    incrementar() {
      this.contador++
    },

    buscar() {
      if (this.consulta.trim() !== "") {
        this.resultado = this.consulta
        this.consulta = ""
      }
    },

    enviar() {
      if (this.nomeForm.trim() !== "") {
        this.enviado = this.nomeForm
        this.nomeForm = ""
      }
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

.btn-primary {
  margin-top: 12px;
  height: 42px;
  padding: 0 18px;
  border: none;
  border-radius: 8px;
  background: #1D9E75;
  color: white;
  cursor: pointer;
  font-size: 14px;
  font-weight: 500;
  transition: .2s;
}

.btn-primary:hover {
  background: #0F6E56;
}

.resultado {
  margin-top: 14px;
  font-size: 14px;
  color: #444;
}

.label {
  color: #888780;
  margin-right: 6px;
}

.feedback {
  margin-top: 14px;
  padding: 12px;
  background: #eef8f4;
  border-radius: 8px;
  font-size: 14px;
  color: #1a1a18;
}

.success {
  background: #eef8f4;
}

.form-area {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>