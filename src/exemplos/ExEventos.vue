<template>
  <div class="exemplo">
    <h2>Eventos — @click, @keyup, @submit</h2>

    <!-- @click simples -->
    <h3>Contador com @click</h3>
    <button @click="incrementar">Clique aqui</button>
    <p>Total de cliques: {{ contador }}</p>

    <hr />

    <!-- @keyup.enter -->
    <h3>Busca com @keyup.enter</h3>
    <input
      v-model="consulta"
      placeholder="Digite e pressione Enter"
      @keyup.enter="buscar"
    />
    <p v-if="resultado">🔍 Buscando por: <strong>{{ resultado }}</strong></p>

    <hr />

    <!-- @submit.prevent -->
    <h3>Formulário com @submit.prevent</h3>
    <form @submit.prevent="enviar">
      <input v-model="nomeForm" placeholder="Seu nome" />
      <button type="submit">Enviar</button>
    </form>
    <p v-if="enviado">✅ Formulário enviado por: <strong>{{ enviado }}</strong></p>
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
.exemplo { font-family: Arial, sans-serif; padding: 16px; }
input { padding: 8px; border: 1px solid #ccc; border-radius: 4px; margin-right: 8px; }
button { padding: 8px 14px; background-color: #42b883; color: white; border: none; border-radius: 4px; cursor: pointer; }
button:hover { background-color: #33a06f; }
hr { margin: 20px 0; }
h3 { color: #333; margin-bottom: 8px; }
</style>