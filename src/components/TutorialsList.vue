<template>
<div class="container text-center">
  <div class="row justify-content-start">
     <div class="col-12">
    <div class="col-4 d-flex">
  <button type="button" class="btn btn-primary me-2">Pesquisar</button>
  <input type="text" class="form-control" placeholder="Pesquisar" aria-label="Username" aria-describedby="basic-addon1">
</div>

      <h3>Contatos</h3>
      <table class="table">
  <thead>
    <tr>
      <th scope="col">Nome</th>
      <th scope="col">Email</th>
      <th scope="col">Numero</th>
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
      currentTutorial: {
        descricao: '',
        estilo: '',
        unidade: ''
      },
      currentIndex: -1,
      submitted: false,
      responseMessage: ''
    };
  },
  methods: {
    Listar() {
      objService.getAll()
        .then(response => {
          this.tutorials = response.data;
          console.log(response.data);
        })
        .catch(e => {
          console.log(e);
        });
    },

    refreshList() {
      this.Listar();
      this.currentTutorial = {
        descricao: '',
        estilo: '',
        unidade: ''
      };
      this.currentIndex = -1;
    },
    
    PesquisarContato() {
      objService.findByTitle(this.title)
        .then(response => {
          this.tutorials = response.data;
          console.log(response.data);
        })
        .catch(e => {
          console.log(e);
        });
    }
  },
  mounted() {
    this.Listar();
  },
};
</script>
