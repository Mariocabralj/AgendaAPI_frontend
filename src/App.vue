<template>
  <div id="app">
    <nav class="navbar navbar-expand navbar-dark bg-info">
      <router-link to="/" class="navbar-brand">AGENDA DE CONTATOS</router-link>
      <div class="navbar-nav mr-auto">
        <li class="nav-item">
          <router-link to="/listar-produtos" class="nav-link" style="color: white">Inicio</router-link>
        </li>
        <li class="nav-item">
          <router-link to="/adicionar-contato" class="nav-link">Adicionar Contato</router-link>
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
  name: "app"
};
</script>
