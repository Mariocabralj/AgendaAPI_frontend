<template>
  <div class="container text-center">
    <div class="row justify-content-start">
      <div class="col-12">
        <div class="col-4 d-flex">
          <!-- Botão Pesquisar com novo estilo -->
          <button
            type="button"
            class="btn btn-pesquisar me-2"
            @click="PesquisarContato"
          >
            Pesquisar
          </button>
          <!-- Campo de entrada para pesquisa -->
          <input
            type="text"
            class="form-control"
            placeholder="Pesquisar"
            aria-label="Pesquisar"
            aria-describedby="basic-addon1"
            v-model="title"
          />
        </div>

        <h3>Contatos</h3>
        <table class="table">
          <thead>
            <tr>
              <th scope="col">Nome</th>
              <th scope="col">Email</th>
              <th scope="col">Número</th>
              <th scope="col">Data do Cadastro</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="(agendaInfos, index) in tutorials"
              :key="index"
              :class="{ active: index == currentIndex }"
            >
              <td>{{ agendaInfos.nome }}</td>
              <td>{{ agendaInfos.email }}</td>
              <td>{{ agendaInfos.telefone }}</td>
              <td>{{ agendaInfos.DataCriacao }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import objService from "../services/TutorialDataService";

export default {
  name: "tutorials-list",
  data() {
    return {
      tutorials: [],
      title: "",
      currentTutorial: {
        descricao: "",
        estilo: "",
        unidade: "",
      },
      currentIndex: -1,
      submitted: false,
      responseMessage: "",
    };
  },
  methods: {
    Listar() {
      objService
        .getAll()
        .then((response) => {
          this.tutorials = response.data;
          console.log(response.data);
        })
        .catch((e) => {
          console.log(e);
        });
    },

    refreshList() {
      this.Listar();
      this.currentTutorial = {
        descricao: "",
        estilo: "",
        unidade: "",
      };
      this.currentIndex = -1;
    },

    PesquisarContato() {
      objService
        .findByTitle(this.title)
        .then((response) => {
          this.tutorials = response.data;
          console.log(response.data);
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
  mounted() {
    this.Listar();
  },
};
</script>

<style>
.btn-pesquisar {
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 20px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.btn-pesquisar:hover {
  background-color: #0056b3;
  transform: scale(1.05);
}

.btn-pesquisar:active {
  background-color: #004085;
}

.form-control {
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 10px;
  font-size: 16px;
}

.form-control:focus {
  border-color: #007bff;
  outline: none;
  box-shadow: 0 0 5px rgba(0, 123, 255, 0.5);
}
</style>
