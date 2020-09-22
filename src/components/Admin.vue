<template>
  <div class="profile-container">
    <ul>
      <li>
        <strong>NOME:</strong>
        <p>{{ admin.nome }}</p>

        <strong>STATUS:</strong>
        <p>{{ admin.status }}</p>
      </li>
      <li>
        <strong>NOME:</strong>
        <p>{{ admin.nome }}</p>

        <strong>STATUS:</strong>
        <p>{{ admin.status }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    admin: Object,
  },
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
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 24px;
  list-style: none;
}

.profile-container ul li {
  background: #202024;
  padding: 24px;
  border-radius: 8px;
  position: relative;
}

.profile-container ul li strong {
  display: block;
  margin-bottom: 16px;
  color: #e1e1e6;
}

.profile-container ul li p + strong {
  margin-top: 32px;
}

.profile-container ul li p {
  color: #737380;
  line-height: 21px;
  font-size: 16px;
}

@media (max-width: 720px) {
  .profile-container ul {
    grid-template-columns: repeat(1, 1fr);
  }
}
</style>
