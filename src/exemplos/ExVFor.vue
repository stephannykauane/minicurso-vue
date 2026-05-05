<template>
  <div class="wrap">
    <div class="card">
      <p class="titulo">v-for</p>
      <p class="subtitulo">
        Renderizando elementos repetidamente a partir de arrays.
      </p>

      <!-- EXPLICAÇÃO -->
      <section class="bloco destaque">
        <p>
          O <code>v-for</code> percorre uma coleção de dados e repete
          automaticamente um bloco HTML para cada item encontrado.
        </p>
      </section>

      <!-- ARRAY SIMPLES -->
      <section class="bloco">
        <div class="bloco-header">
          <span class="badge">1</span>
          <h3>Array simples</h3>
        </div>

        <p class="descricao">
          Aqui o Vue percorre um array de frutas e cria um card para cada item.
        </p>

        <div class="grid">
          <div
            class="item-card"
            v-for="(fruta, index) in frutas"
            :key="index"
          >
            <span class="indice">#{{ index + 1 }}</span>
            <span class="nome">{{ fruta }}</span>
          </div>
        </div>
      </section>

      <!-- ARRAY DE OBJETOS -->
      <section class="bloco">
        <div class="bloco-header">
          <span class="badge">2</span>
          <h3>Array de objetos</h3>
        </div>

        <p class="descricao">
          Também podemos iterar objetos mais complexos, como produtos de uma loja.
        </p>

        <div class="lista-produtos">
          <div
            class="produto-card"
            v-for="produto in produtos"
            :key="produto.id"
          >
            <div>
              <p class="produto-nome">{{ produto.nome }}</p>
              <p class="produto-id">
                ID: {{ produto.id }}
              </p>
            </div>

            <strong class="preco">
              R$ {{ produto.preco.toFixed(2) }}
            </strong>
          </div>
        </div>
      </section>

      <!-- CONTADOR -->
      <section class="bloco resumo">
        <p>
          Foram renderizados
          <strong>{{ frutas.length }}</strong> itens de frutas e
          <strong>{{ produtos.length }}</strong> produtos automaticamente.
        </p>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      frutas: [
        "🍎 Maçã",
        "🍌 Banana",
        "🍇 Uva",
        "🍊 Laranja"
      ],

      produtos: [
        {
          id: 1,
          nome: "Teclado",
          preco: 129.90
        },
        {
          id: 2,
          nome: "Mouse",
          preco: 79.90
        },
        {
          id: 3,
          nome: "Monitor",
          preco: 899.00
        }
      ]
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
  max-width: 720px;
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

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 10px;
}

.item-card {
  background: white;
  border: 1px solid #ecebe7;
  border-radius: 10px;
  padding: 1rem;
}

.indice {
  display: block;
  font-size: 12px;
  color: #888780;
  margin-bottom: 6px;
}

.nome {
  font-weight: 500;
}

.lista-produtos {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.produto-card {
  display: flex;
  justify-content: space-between;
  align-items: center;

  background: white;
  border: 1px solid #ecebe7;
  border-radius: 10px;
  padding: 1rem;
}

.produto-nome {
  font-weight: 500;
}

.produto-id {
  font-size: 12px;
  color: #888780;
  margin-top: 4px;
}

.preco {
  color: #1D9E75;
}

.resumo {
  text-align: center;
  background: #f8f8f7;
}

code {
  background: white;
  padding: 2px 6px;
  border-radius: 4px;
}
</style>