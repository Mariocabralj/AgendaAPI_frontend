<template>
  <div class="container">
    <div class="submit-form">
      <div v-if="!submitted">
        <!-- Linha 1: Title e Description -->
        <div class="row">
          <div class="col-md-12">
            <div class="form-group">
              <label for="title">Descrição</label>
              <input
                type="text"
                class="form-control"
                id="title"
                required
                v-model="tutorial.title"
                name="title"
           

              />
              <label for="style">Estilo</label>
              <input
                type="text"
                class="form-control"
                id="style"
                v-model="tutorial.style"
                name="style"
              />

                <label for="style">Unidade</label>
              <input
                type="text"
                class="form-control"
                id="style"
                v-model="tutorial.style"
                name="style"
              />
            </div>
          </div>

        </div>

        <!-- Linha 2: Estilo e Unidade -->
        

        <!-- Botão de Submit -->
        <br>
        <button @click="saveTutorial" class="btn btn-success">Salvar</button>
      </div>

      <div v-else>
        <h4>Salvo com sucesso!</h4>
        <button class="btn btn-success" @click="newTutorial">Add</button>
      </div>
    </div>
  </div>
</template>


<script>
import TutorialDataService from "../services/TutorialDataService";

export default {
  name: "add-tutorial",
  data() {
    return {
      tutorial: {
        id: null,
        title: "",
        description: "",
        published: false
      },
      submitted: false
    };
  },
  methods: {
    saveTutorial() {
      var data = {
        title: this.tutorial.title,
        description: this.tutorial.description
      };

      TutorialDataService.create(data)
        .then(response => {
          this.tutorial.id = response.data.id;
          console.log(response.data);
          this.submitted = true;
        })
        .catch(e => {
          console.log(e);
        });
    },
    
    newTutorial() {
      this.submitted = false;
      this.tutorial = {};
    }
  }
};
</script>

<style>
.submit-form {
  max-width: 300px;
  margin: auto;
}
</style>
