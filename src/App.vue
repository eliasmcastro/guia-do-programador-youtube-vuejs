<template>
  <div id="app">
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

    <h1>Produtos</h1>
    <div v-for="(produto, index) in produtos" :key="produto.pId">
      <p>Contador do loop: {{index}}</p>
      <Produto :pNome="produto.pNome" :pPreco="produto.pPreco" />
      <input type="text" v-model="produto.pPreco" />
      <hr />
    </div>
  </div>
</template>

<script>
import Usuarios from "./components/Usuarios";
import Admin from "./components/Admin";
import Produto from "./components/Produtos";

export default {
  name: "App",
  data() {
    return {
      status: "Inativo",
      admin: {
        nome: "Nome do Admin",
        status: "Ativo",
      },
      produtos: [
        {
          pId: 1,
          pNome: "Celular",
          pPreco: "50",
        },
        {
          pId: 2,
          pNome: "TV",
          pPreco: "150",
        },
        {
          pId: 3,
          pNome: "Notebook",
          pPreco: "200",
        },
        {
          pId: 4,
          pNome: "Video Game",
          pPreco: "180",
        },
      ],
    };
  },
  components: {
    Usuarios,
    Admin,
    Produto,
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
  margin: 10px 0;
}

button {
  cursor: pointer;
}

.button {
  width: 120px;
  height: 60px;
  background: #e02041;
  border: 0;
  border-radius: 8px;
  color: #fff;
  font-weight: 700;
  margin-top: 16px;
  display: inline-block;
  text-align: center;
  text-decoration: none;
  font-size: 18px;
  line-height: 60px;
  transition: filter 0.2s;
}

.button:hover {
  filter: brightness(90%);
}

#app {
  width: 100%;
  max-width: 1080px;
  padding: 0 30px;
  margin: 32px auto;
}

#app h1 {
  text-align: center;
  margin-bottom: 20px;
}
</style>
