<template>
  <div id="app">
    <h1>Produtos</h1>
    <div class="produto-cadastro-container">
      <input type="text" v-model="produtoNome" placeholder="Nome">
      <input type="number" v-model.number="produtoPreco" placeholder="Preço">
      <button class="button" @click="addProduto">Cadastrar</button>
    </div>
    <small class="nomeObrigatorio" v-show="produtoNomeErro">Nome do produto é obrigatório</small>
    <hr>
    <h3>Produtos Cadastrados</h3>
    <p v-if="produtos.length <= 0">Nenhum produto cadastrado...</p>
    <div v-else class="produto-container">
      <div v-for="(produto, index) in produtos" :key="produto.pId">
        <Produtos :pPosicao="index" :pNome="produto.pNome" :pPreco="produto.pPreco" @eventRemoveProduto="removeProduto($event)" />
      </div>
    </div>

    <h1>Usuários</h1>
    <select name="status" id="status" v-model="status">
      <option value="Ativo" selected>Ativo</option>
      <option value="Inativo">Inativo</option>
    </select>

    <Usuarios
      nome="Elias"
      descricao="Programador"
      :idade="25"
      :status="status"
      v-if="status === 'Ativo'"
    />
    <Usuarios nome="Lucas" descricao="Professor" :idade="35" :status="status" />

    <h1>Admin</h1>
    <Admin :admin="admin" />
  </div>
</template>

<script>
import Usuarios from './components/Usuarios';
import Admin from './components/Admin';
import Produtos from './components/Produtos';

export default {
  name: 'App',
  components: {
    Usuarios,
    Admin,
    Produtos,
  },
  data() {
    return {
      produtoNome: '',
      produtoNomeErro: false,
      produtoPreco: 0,
      produtos: [
        {
          pId: 1,
          pNome: 'Celular',
          pPreco: 50,
        },
        {
          pId: 3,
          pNome: 'Notebook',
          pPreco: 200,
        },
        {
          pId: 4,
          pNome: 'Video Game',
          pPreco: 180,
        },
      ],
      status: 'Inativo',
      admin: {
        nome: 'Nome do Admin',
        status: 'Ativo',
      },
    };
  },
  methods: {
    addProduto() {
      if (this.produtoNome.trim() === '') {
        this.produtoNomeErro = true
        return
      }

      this.produtos.push({
        pId: this.produtos.length + 1,
        pNome: this.produtoNome,
        pPreco: this.produtoPreco
      })

      this.produtoNome = ''
      this.produtoNomeErro = false
      this.produtoPreco = 0
    },
    removeProduto($event) {
      this.produtos.splice($event.pPosicao, 1)
    }
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Roboto:400,500,700&display=swap");
* {
  margin: 0;
  padding: 0;
  outline: 0;
  box-sizing: border-box;
}

body {
  font: 400 14px Roboto, sans-serif;
  background: #f0f0f5;
  -webkit-font-smoothing: antialiased;
}

input,
select {
  width: 100%;
  height: 60px;
  font: 400 18px Roboto, sans-serif;
  color: #333;
  border: 1px solid #dcdce6;
  border-radius: 8px;
  padding: 0 24px;
  margin-bottom: 10px;
}

hr {
  margin: 20px 0;
}

button {
  cursor: pointer;
  width: 120px;
  height: 60px;
  background: #e02041;
  border: 0;
  border-radius: 8px;
  color: #fff;
  font-weight: 700;
  display: inline-block;
  text-align: center;
  text-decoration: none;
  font-size: 14px;
  line-height: 60px;
  transition: filter 0.2s;
  padding: 0 10px;
}

button:hover {
  filter: brightness(90%);
}

#app {
  width: 100%;
  max-width: 1080px;
  padding: 0 30px;
  margin: 32px auto;
}

#app h1, h3 {
  text-align: center;
  margin-bottom: 20px;
}

.produto-cadastro-container {
  display: flex;
  justify-content: space-around;
}

.produto-cadastro-container input + input {
  margin: 0 10px;
}

.produto-cadastro-container button {
  flex-grow: 2;
}

.nomeObrigatorio {
  color: red;
}

.produto-container {
  width: 100%;
  max-width: 1080px;
  margin: 32px auto;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 24px;
}

@media (max-width: 720px) {
  .produto-container {
    grid-template-columns: repeat(1, 1fr);
  }
}
</style>
