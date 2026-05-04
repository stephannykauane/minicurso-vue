# 🟢 Minicurso Vue.js — Do zero ao primeiro projeto!

Repositório oficial do minicurso Vue.js. Contém os exemplos práticos de cada conceito abordado e o projeto final da lista de tarefas.

---

## 🚀 Como rodar o projeto

```bash
# 1. Clone o repositório
git clone https://github.com/stephannykauane/minicurso-vue.git

# 2. Entre na pasta
cd minicurso-vue

# 3. Instale as dependências
npm install

# 4. Inicie o servidor de desenvolvimento
npm run dev
```

Acesse **http://localhost:5173/** no navegador.

---

## 📁 Estrutura do projeto

```
src/
├── App.vue                          ← Projeto final: Lista de Tarefas
│
├── exemplos/                        ← Exemplos de cada conceito do curso
│   ├── ExInterpolacaoVModel.vue     ← Interpolação {{ }} e v-model
│   ├── ExVBind.vue                  ← v-bind (atributos dinâmicos)
│   ├── ExVIfVShow.vue               ← v-if, v-else-if, v-else e v-show
│   ├── ExVFor.vue                   ← v-for (listas)
│   └── ExEventos.vue                ← @click, @keyup.enter, @submit.prevent
│
└── components/                      ← Componentes reutilizáveis
    └── BotaoAcao.vue                ← Criado ao vivo durante o curso (pai/filho)
```

---

## 📚 Conteúdo dos exemplos

| Arquivo | Conceito |
|---|---|
| `ExInterpolacaoVModel.vue` | Exibir dados com `{{ }}` e ligar campos com `v-model` |
| `ExVBind.vue` | Vincular atributos HTML a variáveis com `:atributo` |
| `ExVIfVShow.vue` | Mostrar/ocultar elementos com condições |
| `ExVFor.vue` | Iterar sobre listas de strings e objetos |
| `ExEventos.vue` | Capturar eventos do usuário com `@evento` |

---

## ⚙️ Para usar um exemplo

Para visualizar um exemplo específico, abra o `src/main.js` e substitua a importação do `App`:

```js
// Troque esta linha:
import App from './App.vue'

// Por um dos exemplos, por exemplo:
import App from './exemplos/ExVFor.vue'
```

Salve o arquivo e o navegador atualizará automaticamente.

---

> Mini curso ministrado por **Eduardo Augusto Oliveira Goulart** e **Stephanny Kauane Oliveira Amaral**.