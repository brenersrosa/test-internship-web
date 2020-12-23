<template>
  <div id="app">
    <div class="title-container">
      <h1>Lista de usuários cadastrados</h1>
    </div>

    <div class="cards-container">
      <div class="card" v-for="user of users" :key="user.id">
        <div class="name-container">
          <label>Nome:</label>
          <h2>{{ user.name }}</h2>
        </div>

        <div class="cpf-container">
          <label>CPF.:</label>
          <p>{{ user.cpf }}</p>
        </div>

        <div class="date-container">
          <label>Data de nascimento:</label>
          <p>{{ user.dateOfBirth }}</p>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
  import Users from './services/users';

  export default {
    data() {
      return {
        users: []
      }
    },

    mounted() {
      Users.list().then(response => {
        console.log(response.data)
        this.users = response.data;
      })
    }
  }
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  html {
    background: #D81159;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    margin: 4rem;
    display: flex;
    flex-direction: column;
    align-content: flex-start;
    align-items: center;
    justify-content: center;
  }

  .title-container {
    margin-bottom: 3.4rem;
  }

  .cards-container {
    display: flex;
    flex-wrap: wrap;
    align-content: flex-start;
    align-items: center;
    justify-content: center;
    max-width: 104rem;
  }

  h1 {
    font-size: 1.5rem;
    text-transform: uppercase;
    font-weight: 900;
    color: #FFFCF2;
  }

  .card {
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    width: 20rem;
    height: 24rem;
    background: linear-gradient(to bottom right, #FFFCF2, #FFFCF2);
    margin: 0.625rem;
    padding: 0 1rem;
    border-radius: 1rem;
    box-shadow: 0.375rem 0.375rem 0.625rem rgba(0, 0, 0, 0.7);
  }

  .card:hover {
    transform: scale(1.025);
    transition: ease-in-out .4s;
  }

  .name-container,
  .cpf-container,
  .date-container {
    width: 100%;
    display: flex;
    flex-direction: column;
  }

  label {
    font-size: 1rem;
    color: #9C98A6;
    padding-bottom: 0.25rem;
    /* font-style: italic; */
  }

  h2 {
    font-size: 1.25rem;
    color: #32264D;
    text-transform: uppercase;
    font-weight: 900;
  }

  p {
    font-size: 1.25rem;
    color: #32264D;
  }
</style>
