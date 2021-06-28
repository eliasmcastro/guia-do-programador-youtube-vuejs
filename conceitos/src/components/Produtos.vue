<template>
  <ul>
    <li :class="{ cinza: !corPadrao, azul: corPadrao }">
      <p>Contador do loop: {{ pPosicao }} <span class="remover" @click="emitEventRemoveProduto">X</span></p>
      <strong>NOME:</strong>
      <p>{{ pNome | nomeMaisculo }}</p>

      <strong>PREÇO:</strong>
      <p>{{ pPreco }}</p>

      <strong>Código:</strong>
      <p>{{ codigoProduto }}</p>

      <p class="acao"><button class="button" @click="mudarCor">Mudar Cor</button></p>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'Produtos',
  props: {
    pPosicao: Number,
    pNome: String,
    pPreco: Number,
  },
  data() {
    return {
      corPadrao: false,
    };
  },
  methods: {
    mudarCor() {
      this.corPadrao = !this.corPadrao;
    },
    emitEventRemoveProduto() {
      this.$emit('eventRemoveProduto', {pPosicao: this.pPosicao, component: this})
    }
  },
  filters: {
    nomeMaisculo (value) {
      return value.toUpperCase()
    }
  },
  computed: {
    codigoProduto() {
      return (this.pPosicao + this.pNome + this.pPreco)
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
}

ul li {
  padding: 24px;
  border-radius: 8px;
  position: relative;
}

ul li strong {
  display: block;
  margin-bottom: 16px;
  color: #41414d;
}

ul li p + strong {
  margin-top: 32px;
}

ul li p {
  color: #737380;
  line-height: 21px;
  font-size: 16px;
}

.acao {
  margin-top: 10px;
  text-align: right;
}

.cinza {
  background: rgb(190, 190, 190);
}

.azul {
  background: rgb(128, 122, 177);
}

.azul p {
  color: #fff;
}

.remover {
  float: right;
  cursor: pointer;
  background: #202024;
  color: #fff;
  border-radius: 20%;
  padding: 5px;
}
</style>
