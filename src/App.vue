<template>
  <div id="app">
    <nav class="navbar navbar-expand navbar-dark">
      <router-link to="/" class="navbar-brand">AGENDA DE CONTATOS</router-link>
      <div class="navbar-nav mr-auto">
        <li class="nav-item">
          <router-link to="/listar-produtos" class="nav-link"
            >Inicio</router-link
          >
        </li>
        <li class="nav-item">
          <router-link to="/adicionar-contato" class="nav-link"
            >Adicionar Contato</router-link
          >
        </li>
      </div>
    </nav>

    <div class="container mt-3">
      <router-view />
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

body {
  font-family: "Roboto", sans-serif;
}

.navbar {
  background: linear-gradient(90deg, #1e90ff, #87ceeb);
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}

.navbar-brand {
  font-size: 24px;
  font-weight: bold;
  color: white;
  text-shadow: 1px 1px 4px rgba(0, 0, 0, 0.3);
}

.nav-link {
  font-size: 16px;
  color: white;
  margin-right: 15px;
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: #ffd700;
}

.container {
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.1);
}
</style>
