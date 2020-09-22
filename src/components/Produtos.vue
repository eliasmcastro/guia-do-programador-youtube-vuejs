<template>
  <div class="produto-container">
    <ul>
      <li :class="{'cinza' : !corPadrao, 'azul': corPadrao}">
        <strong>NOME:</strong>
        <p>{{ pNome }}</p>

        <strong>PREÇO:</strong>
        <p>{{ pPreco }}</p>
        <button class="button" @click="mudarCor">Mudar Cor</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      corPadrao: false,
    };
  },
  props: {
    pNome: String,
    pPreco: Number,
  },
  methods: {
    mudarCor: function () {
      this.corPadrao = !this.corPadrao;
    },
  },
};
</script>

<style scoped>
.produto-container {
  width: 100%;
  max-width: 1080px;
  margin: 32px auto;
}

.produto-container h1 {
  margin-top: 50px;
  margin-bottom: 24px;
}

.produto-container ul {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  grid-gap: 24px;
  list-style: none;
}

.cinza {
  background: rgb(190, 190, 190);
}
.azul {
  background: rgb(128, 122, 177);
}

.produto-container ul li {
  padding: 24px;
  border-radius: 8px;
  position: relative;
}

.produto-container ul li strong {
  display: block;
  margin-bottom: 16px;
  color: #41414d;
}

.produto-container ul li p + strong {
  margin-top: 32px;
}

.produto-container ul li p {
  color: #737380;
  line-height: 21px;
  font-size: 16px;
}
</style>
