<template>
  <div class="profile-container">
    <ul>
      <li>
        <strong>NOME:</strong>
        <p>{{ nome }} ({{ status }})</p>

        <strong>DESCRIÇÃO:</strong>
        <p>{{ descricao }}</p>

        <strong>IDADE:</strong>
        <p>{{ idade }}</p>

        <strong>COMENTÁRIO:</strong>
        <input type="text" v-model="comentario" />
        <p>{{ comentario }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Usuarios',
  props: {
    nome: String,
    descricao: String,
    idade: Number,
    status: String,
  },
  data() {
    return {
      comentario: 'Altere esse comentário',
    };
  }
};
</script>

<style scoped>
.profile-container {
  width: 100%;
  max-width: 1080px;
  margin: 32px auto;
}

.profile-container h1 {
  margin-top: 50px;
  margin-bottom: 24px;
}

.profile-container ul {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  grid-gap: 24px;
  list-style: none;
}

.profile-container ul li {
  background: #fff;
  padding: 24px;
  border-radius: 8px;
  position: relative;
}

.profile-container ul li strong {
  display: block;
  margin-bottom: 16px;
  color: #41414d;
}

.profile-container ul li p + strong {
  margin-top: 32px;
}

.profile-container ul li p {
  color: #737380;
  line-height: 21px;
  font-size: 16px;
}
</style>
